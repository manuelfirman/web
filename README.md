# Package Web for request and response

## Request Package for Go

El paquete `request` proporciona utilidades para decodificar JSON de los cuerpos de las solicitudes HTTP en estructuras de Go de una manera simple y eficiente.

### Características

- **Validación de Tipo de Contenido**: Asegura que el contenido de la solicitud sea del tipo `application/json` antes de proceder a decodificar.
- **Decodificación de JSON**: Facilita la decodificación del cuerpo de la solicitud JSON directamente en una estructura de Go especificada por el usuario.


---
---

## Response Package for Go

El paquete `response` ofrece un enfoque estandarizado para enviar respuestas de error JSON en aplicaciones web Go. Facilita la creación y el envío de mensajes de error coherentes y bien formados a los clientes de tu API o aplicación web.

### JSON

- **Escribir Respuestas JSON**: Permite escribir respuestas JSON en el cuerpo de una respuesta HTTP con un código de estado específico.
- **Manejo de Respuestas Vacías**: Maneja automáticamente respuestas JSON vacías (nil) devolviendo un código de estado sin contenido.



---

### Error

- **Respuestas de Error Estandarizadas**: Genera respuestas de error JSON con un formato consistente, incluyendo un estado y un mensaje.
- **Flexibilidad en Mensajes de Error**: Permite personalizar el mensaje de error y el código de estado HTTP para adaptarse a diferentes situaciones de error.
- **Función de Formato de Error**: Soporta la creación de mensajes de error formateados, similar a cómo `fmt.Sprintf` maneja los strings.


---

### Text

- **Escribir Respuestas de Texto**: Permite escribir respuestas de texto en el cuerpo de una respuesta HTTP con un código de estado específico.
- **Codificación de Caracteres UTF-8**: Codifica automáticamente el texto con caracteres UTF-8 para manejar caracteres especiales correctamente.

