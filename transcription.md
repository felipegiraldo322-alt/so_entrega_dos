# Resumen Taller Final - Sistemas Operativos  
**Simulación de TLB con política MRU en C**  
Monitor: Juan Esteban – Fecha: 2025  
Enlace de la grabación: https://juhincapieh.notion.site/Taller-11-Asesor-a-Trabajo-2-228fa2d8dde6804a893dcc9831cac3bf

---

## Índice de Segmentos del Video

| # | Tiempo aproximado      | Duración | Tema principal                              |
|---|------------------------|----------|---------------------------------------------|
| 1 | 09:00 – 20:00          | ~11 min  | Introducción y lectura del enunciado        |
| 2 | 20:00 – 35:00          | ~15 min  | Estructura del TLB y uso de memoria (heap) |
| 3 | 35:00 – 55:00          | ~20 min  | Política de reemplazo MRU y hits/misses      |
| 4 | 55:00 – 01:32:00       | ~37 min  | Tiempo, conversiones y cierre               |

---

### Segmento 1 – Introducción y Lectura del Enunciado [09:00 – 20:00]
- Espacio virtual de **32 bits** → direcciones de 0 a 2³²−1 (4 294 967 295).
- Páginas de **4 KB** = **4096 bytes** → **12 bits** de offset.
- Por tanto: **20 bits** para número de página, **12 bits** para desplazamiento.
- Entrada del programa: direcciones en **decimal**, lectura indefinida hasta escribir **s** (minúscula).
- Salida requerida: página (decimal y binario), desplazamiento (decimal y binario), hit/miss, tiempo, etc.

### Segmento 2 – Estructura del TLB y Almacenamiento en Memoria [20:00 – 35:00]
- TLB con **5 entradas**.
- Memoria máxima asignada: **300 bytes** → máx **60 bytes por entrada**.
- **Recomendación de tipos (46 bytes total por entrada)**:
  | Campo                     | Tipo                | Tamaño     |
  |---------------------------|---------------------|------------|
  | Dirección virtual (decimal) | `unsigned int`    | 4 bytes    |
  | Número de página (decimal)  | `unsigned int`    | 4 bytes    |
  | Desplazamiento (decimal)    | `unsigned int`    | 4 bytes    |
  | Página en binario           | `char[21]` (20 + '\0') | 21 bytes |
  | Desplazamiento en binario   | `char[13]` (12 + '\0') | 13 bytes |
  | **Total**                   |                     | **46 bytes** |

- Reserva con `malloc(300)` → obligatorio usar el **heap**.
- No se permiten arrays estáticos para el TLB, todo con punteros.

### Segmento 3 – Política de Reemplazo MRU y Gestión de Hits/Misses [35:00 – 55:00]
- Política: **MRU** (Most Recently Used) → se reemplaza la página **más recientemente usada**.
- Dos formas válidas (elige una):
  1. Reorganizar físicamente las entradas (usando `memcpy`) para que la más reciente quede al final.
  2. Sobrescribir siempre la última posición y llevar control lógico del orden.
- Al producirse reemplazo → imprimir la dirección base (en hexadecimal) de la entrada que se reemplaza.
- Hit → reordenar (la entrada accedida pasa a ser la más reciente).
- Miss → insertar o reemplazar según MRU.

---

### Segmento 4 – Medición de Tiempo, Conversiones y Cierre [55:00 – 01:32:00]
- Medir tiempo con `gettimeofday(&start, NULL)` y `gettimeofday(&end, NULL)`.
- Cálculo del tiempo en segundos:
  ```c
  double tiempo = (end.tv_sec - start.tv_sec) +
                  (end.tv_usec - start.tv_usec) / 1000000.0;


---
### Índice de Segmentos del Video
Funciones obligatorias:
- Decimal → Binario (string)
- Binario (string) → Decimal
- Usar operaciones bitwise (>>, &, <<)

Al final del programa:Cfree(memoria_inicio);
printf("Goodbye\n");
return 0;
Casos especiales:
malloc devuelve NULL → “Error al asignar memoria”
Dirección < 0 o ≥ 2³² → “Page fault”


---
## Tips finales del mentor

Revisar constantemente el enunciado.
No usar librerías prohibidas (preguntar a Harrison si hay restricciones nuevas).
Liberar siempre la memoria.
Forzar el uso de las funciones de conversión aunque no sean estrictamente necesarias.

¡Éxitos con el trabajo final!
Cualquier duda → WhatsApp del mentor.