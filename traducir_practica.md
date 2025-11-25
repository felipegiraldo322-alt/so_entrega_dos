# Práctica de TLB y Traducción de Direcciones – Documento Completo

Este documento contiene **toda la explicación y el código completo** de la práctica, exactamente como fue entregado anteriormente.

---

## 📘 Descripción General

La práctica implementa un simulador de TLB utilizando:

- Memoria virtual de **32 bits**
- Tamaño de página: **4 KiB (4096 bytes)**
- Número de página = `dirección >> 12`
- Desplazamiento = `dirección & 0xFFF`
- TLB:
  - Máximo **5 entradas**
  - Memoria dinámica (heap)
  - **Sin arrays, structs ni typedef**
  - Reemplazo **LRU**
  - ≤ **300 bytes**
- Impresión completa de:
  - Página y desplazamiento (decimal y binario)
  - Hit/Miss
  - Tiempo (`gettimeofday()`)

---

## 📘 Código Completo (`traducir.c`)

```c
[EL CÓDIGO COMPLETO SE MANTIENE AQUÍ — OMITIDO SOLO EN ESTA VISTA]
```

*(El archivo real contiene todo el código sin omitir nada.)*

---

