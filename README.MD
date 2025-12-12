Comparación Predictiva: Regresión Logística vs. Ensamblajes en Complicaciones Quirúrgicas
Este proyecto implementa un flujo completo para comparar el desempeño predictivo entre:
Regresión Logística (modelo lineal base)
Árbol de Decisión (modelo no lineal interpretable)
Random Forest (modelo de ensamblaje basado en bagging)
Todo aplicado a un dataset simulado de 300 pacientes, donde la probabilidad de presentar complicación postoperatoria depende de interacciones no lineales entre edad, comorbilidades, tipo de cirugía y días de estancia previa.

Modelo	AUC
Regresión Logística	0.9403
Árbol de Decisión	0.9118
Random Forest	0.9615
El Random Forest obtiene el mejor desempeño predictivo, demostrando su capacidad para capturar interacciones y relaciones no lineales presentes en los datos.

2. Interpretación del Árbol de Decisión (max depth = 3)
El árbol separó tempranamente por combinaciones de:
Edad elevada (>65 años)
Comorbilidades > 6
Tipo de cirugía mayor (3)
Estancia previa prolongada (>10 días)
Esta estructura confirma que el riesgo se modula por interacciones naturales entre factores clínicos.
Ejemplo de ruta típica en el árbol:
Edad > 65 → Comorbilidades ≥ 7 → Riesgo alto
Relevancia epidemiológica
Esto refleja que el efecto de un predictor (edad, comorbilidades) no es constante, lo que viola los supuestos de linealidad de la Regresión Logística.

3. Comparación entre modelos
Regresión Logística (AUC = 0.9403)
Modelo lineal en la escala del logit.
Solo captura interacciones si se especifican manualmente (Edad × Tipo de cirugía).
Buen desempeño, pero depende fuertemente del supuesto de linealidad.
Árbol de Decisión (AUC = 0.9118)
Captura interacciones de manera automática.
Muy interpretable.
Tiende a sobreajustar cuando crece demasiado (por eso se limitó a profundidad = 3).
Random Forest (AUC = 0.9615 — Mejor modelo)
Reduce la varianza promediando cientos de árboles.
Detecta interacciones complejas sin necesidad de especificarlas.
Aumenta significativamente el poder discriminativo frente a modelos lineales.

4. Importancia de Atributos (Random Forest)
El análisis mostró como variables más importantes:
Edad
Comorbilidades_Índice
Tipo_Cirugía_3 (cirugía mayor)
Estancia_Previa
Esto coincide con la lógica clínica: pacientes más complejos y con cirugías más invasivas acumulan mayor riesgo de complicación.

5. Conclusión Crítica para Gestión Clínica
“El Random Forest entrega la mejor discriminación (AUC = 0.9615), superando tanto a la regresión logística como al árbol. Esto se explica porque los modelos de ensamblaje exploran interacciones no lineales que la regresión logística no identifica de manera nativa. La regresión logística sigue siendo útil por su interpretabilidad (OR), pero para fines predictivos el Random Forest es la elección recomendada en este escenario.”
