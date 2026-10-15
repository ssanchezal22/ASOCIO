# ASOCIO – Asignación Óptima de Espacios de Trabajo

**Satisfacción del colaborador vs. reglas organizacionales**  
Proyecto de optimización – Departamento de Ingeniería Industrial, Universidad de Antioquia (2025).

📄 **Informe de entrega:** [ASOCIO_OPTIMIZACION_2025.pdf](./ASOCIO_OPTIMIZACION_2025.pdf)

## Resumen

Sistema en Python (Pyomo + solver CBC) que asigna escritorios, días y zonas a los colaboradores de la universidad equilibrando dos objetivos en conflicto mediante una **optimización en dos etapas**:

1. **Modelo F2 – Colaboradores:** maximiza la satisfacción según las preferencias de cada colaborador, respetando asistencia mínima, un colaborador por escritorio y la programación de reuniones grupales.
2. **Modelo F1 – Universidad:** minimiza la dispersión de los grupos entre zonas y las penalizaciones por baja presencialidad (P1) y por colaboradores aislados en una zona sin su grupo (P2).
3. **Restricción épsilon:** F1 se resuelve exigiendo un nivel mínimo de satisfacción (ε) definido por el usuario a partir del máximo obtenido en F2.

### Resultados (10 instancias)

| Modelo | Satisfacción | Penalizaciones |
|---|---|---|
| F2 (colaboradores) | 83 % – 91 % | Altas (hasta 201) |
| F1 (universidad) | 34 % – 56 % | Bajas |
| **Épsilon (combinado)** | **66 % – 77 %** | **Muy bajas** |

El modelo épsilon logra el mejor equilibrio: por ejemplo, en la instancia 9 alcanza 68.54 % de satisfacción (vs. 50.49 % en F1) y reduce las penalizaciones en un 88 % frente a F2. El detalle completo, el análisis y la formulación matemática están en el [informe](./ASOCIO_OPTIMIZACION_2025.pdf).

### Uso

El usuario final solo necesita ejecutar `Script_ejecucion_usuario.py`, que guía la carga de la instancia (`.json`), la ejecución y la exportación de resultados (visualizaciones y Excel en `Salidas_usuario`). Se recomiendan ~1 h de resolución para las instancias 1–6 y ~1.5 h para las 7–10.

## Autores

- Juan Diego Arroyave Murillo  |  juan.arroyave14@udea.edu.co  |  linkedin.com/in/juan-diego-arroyave-murillo-41ba08302
- Sebastian Sanchez Alvarez  |  sebastian.sanchez9@udea.edu.co  |  linkedin.com/in/sebastián-sánchez-álvarez-919018237
- Tatiana Ortiz Rojas  |  tatiana.ortizr1@udea.edu.co  |  linkedin.com/in/tatiana-ortiz-rojas-419b0b26b

## Licencia

Este proyecto está licenciado bajo los términos de la **Apache License 2.0**.  
Puedes ver los detalles completos en el archivo [LICENSE](./LICENSE).

## DescripcionReto.docx.pdf

Descripción y espeficicación completa del reto desarrollado

## Optimizador CBC

Para este proyecto se hizo uso del optimizador CBC desarrollado por Coin-or el release Cbc-releases.2.10.12-windows-2022-msvs-v17-Release-x64 el cual se encuentra en el repositorio https://github.com/coin-or/Cbc/releases

## requerements.txt

Contiene las librerias necesarias que se deben instalar para correr el sistema

## Funciones.py

Contiene las funciones desarrolladas para realizar calculos y metricas de los modelos, exportacion e importacion de los modelos.

## Funciones_modelos.py

Contiene los modelos F1 y F2 empaquetados en funciones

## Script_ejecucion_usuario.py y Salidas_usuario

Hace uso de los modelos empaquetados para crear la experiencia de usuario, los resultados de las visualizaciones y el excel con la programacion se exportan en la carpteta Salidas_usuario

## Instances

Contiene las instancias con las que es posible correr los diferentes modelos

## Despliegue.py y Model_outputs

Despliegue del modelo F1 crudo (solo intereses de la universidad), todos los resultados de este modelo son exportados en la carpeta Model_outputs

## Despliegue_epsilon.py, Model_outputs_epsilon y Model_outputs_F2

Despliegue del modelo F2 crudo (solo intereses de los colaboradores) y el modelo epsilon. Los resultados de ambos modelos se exportan hacia las carpetas Model_outputs_F2 y Model_outputs_epsilon respectivamente
