# 🚍 Sistema GPS de Paradas y Rutas de Transporte

Aplicación web progresiva (PWA) de una sola página (*Single Page Application*), ligera y altamente optimizada para dispositivos móviles. Esta herramienta está diseñada para el **levantamiento en campo de coordenadas GPS, gestión de paradas y ordenamiento secuencial de rutas de transporte público**.

---

## 🚀 Funcionalidades Principales

* **Geolocalización y Calibración de Alta Precisión:** Utiliza la API de geolocalización nativa del dispositivo. Al marcar una parada, realiza un muestreo de hasta 6 lecturas consecutivas para filtrar y seleccionar la coordenada con mayor precisión (buscando una tolerancia ideal de $\le 5$ metros).
* **Catálogo de Rutas Dinámico:** Permite crear, visualizar y eliminar rutas de transporte personalizadas. Toda la información se almacena de forma persistente en el navegador utilizando `localStorage`, por lo que no se pierde al recargar la página.
* **Asociación Múltiple y Secuencia Automática:** Una parada puede pertenecer a una o varias rutas al mismo tiempo. El sistema calcula de forma automática y correlativa el número de orden (*secuencia*) de la parada para cada ruta específica.
* **Gestión Inteligente de Secuencias:** Si se elimina una parada registrada previamente, el sistema recalcula y reordena automáticamente la secuencia numérica de las paradas restantes en las rutas afectadas.
* **Referencias Opcionales:** Permite añadir un nombre descriptivo o punto de referencia personalizado a cada parada (por ejemplo: *"Esquina Plaza Bolívar / Frente al Liceo"*).
* **Exportación Estructurada en CSV:** Genera un archivo CSV listo para procesar en hojas de cálculo (Excel, Google Sheets) o SIG/GIS con los siguientes campos:
  * `id_registro`: Identificador único por línea de ruta.
  * `id_parada`: Número correlativo global de la parada.
  * `nombre_parada`: Referencia asignada.
  * `ruta`: Nombre de la ruta asociada.
  * `orden_secuencia_ruta`: Número de orden que ocupa la parada dentro de esa ruta.
  * `latitud` y `longitud`: Coordenadas GPS exactas.
  * `precision_m`: Margen de error en metros de la lectura GPS.
  * `fecha` y `hora`: Marca temporal exacta del registro.
* **Compartir Directo (Web Share API):** Permite compartir el archivo CSV generado directamente a través de aplicaciones móviles (Telegram, WhatsApp, correo electrónico) o descargarlo localmente.

---

## 📱 Guía de Uso en Campo

1. **Pantalla de Inicio (GPS):** 
   * Al abrir la aplicación en tu teléfono, verás una pantalla de bienvenida.
   * Pulsa el botón **"Activar / Permitir Ubicación GPS"** y concede los permisos de ubicación requeridos por tu navegador.
2. **Gestionar el Catálogo de Rutas:** 
   * En la pantalla principal, presiona el botón **"➕ Gestionar Rutas"**.
   * Escribe el nombre de tu ruta (ej. *Ruta 01 - Centro*) y presiona *"Añadir Ruta al Catálogo"*.
   * Cuando termines de registrar tus rutas, pulsa **"✓ Finalizar y Volver a Marcar Paradas"**.
3. **Marcar una Parada en el Recorrido:**
   * Selecciona con un check la o las rutas que transitan por la parada actual.
   * *(Opcional)* Escribe una referencia en el campo *"Nombre/Referencia de Parada"*.
   * Presiona el botón verde **"📍 MARCAR PARADA (CALIBRAR GPS)"**. El sistema muestreará los satélites durante unos segundos hasta guardar la posición óptima.
4. **Exportar o Enviar los Datos:** 
   * En la parte inferior de la pantalla principal, selecciona **"Compartir / Enviar a Telegram"** o **"Descargar Archivo CSV"** para extraer los datos recopilados al finalizar la jornada.
