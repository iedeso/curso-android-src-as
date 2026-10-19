# Prompt para Claude Code: TV Xiaomi más fluida (basado en https://tv.cobanov.dev/)

Úsalo en un PC con Claude Code y `adb` instalado, en la misma red que la TV.
Rellena MODELO e IP y pégalo como primer mensaje.

---

Tengo una TV Xiaomi, modelo: MODELO, con IP: IP_DE_LA_TV. Quiero que vaya más fluida.

Reglas:
1. Conecta con `adb connect IP_DE_LA_TV:5555` (si es Android 11+ y pide código, usa `adb pair`). Yo acepto el aviso en la TV.
2. Solo puedes usar `pm disable-user --user 0`. Prohibido desinstalar, hacer root o flashear.
3. Mide antes y después: `dumpsys meminfo`, `pm list packages -s`, `pm list packages -d`.
4. Clasifica los paquetes en: claramente basura / los decido yo / intocables. Enséñame la lista antes de tocar nada.
5. Nunca desactives un paquete que no sepas identificar. Intocables: menú de entradas/fuentes, actualizaciones del sistema, servicios HDMI/antena, mando, Play Services, Play Store, ubicación, teclado en pantalla y launcher.
6. Si hay que desactivar el launcher de Google, instala antes FLauncher y ponlo como predeterminado.
7. Desactiva como máximo 10 paquetes por tanda. Tras cada tanda me pides probar: botón de entradas, cambio HDMI, apps de streaming, audio y teclado.
8. Registra todo en `tv-debloat/disabled.txt` y `tv-debloat/DEBLOAT-LOG.md` (qué cambió y el comando para deshacerlo).
9. Pon las animaciones al 0.5: `settings put global window_animation_scale 0.5` (y `transition_animation_scale`, `animator_duration_scale`).
10. Limpia cachés con `pm trim-caches 999G` y reinicia.

Deshacer: `adb shell pm enable <paquete>`.
