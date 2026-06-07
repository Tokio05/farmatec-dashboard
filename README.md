# F@armaTec - Dashboard de Validación Farmacodinámica

Este repositorio contiene el código fuente de la plataforma web interactiva desarrollada para **F@armaTec en línea**. La aplicación funciona como un entorno de validación híbrido, combinando la selección preliminar de compuestos químicos mediante Inteligencia Artificial con el rigor del cálculo numérico clásico para el ajuste de curvas dosis-respuesta.

El objetivo principal es resolver un sistema lineal sobredimensionado incompatible para estimar con precisión matemática los parámetros cinéticos de un fármaco candidato.

## Características del Proyecto

* **Motor de Cálculo en Tiempo Real:** Implementación nativa en JavaScript de las Ecuaciones Normales de Gauss utilizando mínimos cuadrados ordinarios (MCO).
* **Visualización Interactiva:** Renderizado dinámico de la curva sigmoidea de Hill frente a la nube de puntos mediante la API de Chart.js.
* **Módulo de Diagnóstico Analítico:** Gráfico complementario de dispersión de residuos para auditar la falta de homocedasticidad y evaluar críticamente el sesgo estadístico.
* **Diseño Minimalista y Estético:** Interfaz optimizada ("aesthetic") maquetada con Tailwind CSS en modo oscuro, facilitando la comprensión y la transferencia de resultados tanto a perfiles técnicos como clínicos.

## Fundamento Matemático

La relación macroscópica de saturación biológica se modela mediante la **Ecuación de Hill**:

E(C) = (Emax * C^n) / (EC50^n + C^n)

Dado un conjunto masivo y sobredimensionado de m = 150 muestras experimentales ruidosas, el operador no lineal se transforma mediante una biyección logarítmica en un sistema lineal de la forma Ax = b. 

Debido a la presencia de ruido, el vector de datos no pertenece al espacio columna de la matriz de diseño. La solución óptima única (x_hat) se halla proyectando ortogonalmente dicho vector mediante las Ecuaciones Normales:

A^T * A * x_hat = A^T * b

### El Sesgo de la Desigualdad de Jensen
El software expone de forma transparente una subestimación sistemática en los estimadores calculados. Al aplicar una función estrictamente cóncava (logaritmo) sobre un entorno con ruido simétrico, la esperanza matemática del error se desplaza negativamente, un fenómeno analítico crítico que se discute en la documentación del proyecto.

## Lenguajes y Paquetes

* HTML5
* Tailwind CSS (vía CDN)
* JavaScript
* Chart.js (vía CDN)

## Instalación y Despliegue

Al tratarse de una Single Page Application (SPA), el proyecto es muy ligero. No requiere servidores ni entornos de ejecución pesados.

1. Clona este repositorio en tu máquina local:
   git clone https://github.com/tu-usuario/farmatec-dashboard.git

2. Abre el archivo `index.html` en cualquier navegador web moderno (Chrome, Firefox, Edge, Safari) haciendo doble clic sobre él.

## Licencia e Información de Entrega

Este proyecto ha sido desarrollado como parte de las entregas de la asignatura de Álgebra Lineal y Multilineal del Grado en Matemática Computacional en la UNIR. 

* **Autor:** Héctor González Elvira
* **Fecha de Despliegue:** Mayo de 2026
