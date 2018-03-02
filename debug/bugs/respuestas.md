Si no agregamos el flag -g de debug, dentro de gdb tenemos los errores:
No hay tabla de símbolos cargada. Use la orden «file».
y al poner, por ejemplo, file add_array_nobugs_c.o, obtenemos:
Leyendo símbolos desde /home/alumno/Escritorio/WTPC/HOdebug-profile/debug/bugs/add_array_nobugs_c.o...(no se encontraron símbolos de depuración)hecho.
Al correrlo con el flag -g se pueden realizar los comandos de debug de gdb sobre las variables.
Respecto a las flags de optimización parece ser lo mas recomendable utilizar -O0 si el código no resulta extremadamente lento (ver referencia: https://stackoverflow.com/questions/7493947/whats-the-best-g-optimization-level-when-building-a-debug-target)
El Wall da pistas sobre si el error es de linkeo o de compilación y además avisa sobre los errores de varibles no inicializadas.