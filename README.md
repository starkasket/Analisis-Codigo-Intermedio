# Analisis-Codigo-Intermedio
Este proyecto detalla el proceso de generación de código intermedio y los beneficios que se obtienen a través de la optimización que realiza.

# Generación de Código Intermedio 
Después de que el compilador completa el análisis semántico, el compilador posee una estrcutra interna del programa (por ejemplo, un árbol sintáctico). A partir de esta estructura se realiza la traducción al **código intermedio** mediante un proceso llamado _generación de código intermedio_.

_Proceso paso a paso_:
1. **Entrada**: árbol sintáctico + tabla de símbolos + tipos verificados.
2. **Recorrido del árbol**: el compilador recorre el programa nodo por nodo.
3. **Descomposición de expresiones**: las expresiones complejas se separan en operaciones simples.
4. **Creación de temporales**: se generan variables temporales para almacenar resultados intermedios.
5. **Salida**: lista estructurada de instrucciones de código intermedio.

**_EJEMPLO_**:
Código:
_x = (a + b) * c_
Código intermedio:
_v1 = a + b
v2 = v1 * c
x = v2_

**Beneficios del uso del IR para la optimización**:
El código intermedio es ideal para optimizar porque es independiente del hardware y es simple estructuralmente. Esto permite aplicar mejoras antes de generar instrucciones reales del procesador. 

_Eliminación de código muerto_:
Consiste en eliminar instrucciones que no afectan el resultado final
_Ejemplo: 
v1 = a + b
v2 = 5
return v1_
Como la asignación de _v1_ nunca se usa, se elimina. Esto reduce el tamaño del programa y mejora el rendimiento.

_Propagación de constantes:_
Sustituye variables cuyo valor es conocido por el valor directamente.
_Ejemplo:
x = 5
y = x + 3
Optimizado:
y = 5 + 3
Luego:
y = 8_
Esto reduce cálculos en tiempo de ejecución y permite nuevas optimizaciones posteriores.

_Simplificación algebraíca:_
Transforma expresiones para hacerlas más simples.
_Ejemplos:
x = y * 1 --> x = y
x = z + 0 --> x = z_

_Reordenamiento de instrucciones:_
El compilador puede reorganizar operaciones para reducir dependencias, y mejorar uso de registros

Optimizar en código máquina es más difícil que en IR porque depende de cada arquitectura, hay menos información semántica y es más complejo analizar dependencias. Optimizar en IR permite aplicar las mismas optimizaciones a cualquier procesador, reutilziar algoritmos de optimización, y generar código final más eficiente sin repetir trabajo.


