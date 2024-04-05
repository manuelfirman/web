# Package Web for request and response

## Request Package for Go

El paquete `request` proporciona utilidades para decodificar JSON de los cuerpos de las solicitudes HTTP en estructuras de Go de una manera simple y eficiente.

### Características

- **Validación de Tipo de Contenido**: Asegura que el contenido de la solicitud sea del tipo `application/json` antes de proceder a decodificar.
- **Decodificación de JSON**: Facilita la decodificación del cuerpo de la solicitud JSON directamente en una estructura de Go especificada por el usuario.

### Uso

Para utilizar las funcionalidades del paquete `request`, primero importa el paquete en tu proyecto Go.

```go
import "github.com/manuelfirman/web/request"
```

#### Decodificando JSON de una Solicitud HTTP
Para decodificar el JSON de una solicitud HTTP en una estructura de Go, utiliza la función JSON:

```go
type myStruct struct {
    Campo1 string `json:"campo1"`
    Campo2 int    `json:"campo2"`
}

err := request.JSON(r, &myStruct)
if err != nil {
    // handle error
}
```

### Errores
* **`ErrRequestContentTypeNotJSON`**: Este error se devuelve si el tipo de contenido de la solicitud no es application/json.
* **`ErrRequestJSONInvalid`**: Se devuelve este error si el cuerpo de la solicitud contiene JSON inválido o si hay un error al decodificar

---
---

## Response Package for Go

El paquete `response` ofrece un enfoque estandarizado para enviar respuestas de error JSON en aplicaciones web Go. Facilita la creación y el envío de mensajes de error coherentes y bien formados a los clientes de tu API o aplicación web.

### JSON

- **Escribir Respuestas JSON**: Permite escribir respuestas JSON en el cuerpo de una respuesta HTTP con un código de estado específico.
- **Manejo de Respuestas Vacías**: Maneja automáticamente respuestas JSON vacías (nil) devolviendo un código de estado sin contenido.

#### Uso

##### Escribiendo una Respuesta JSON

Para enviar una respuesta JSON, utiliza la función `JSON`:

```go
import "github.com/tu_usuario/tu_repositorio/response"

func miHandler(w http.ResponseWriter, r *http.Request) {
    data := map[string]interface{}{
        "mensaje": "Hola mundo",
    }
    response.JSON(w, http.StatusOK, data)
}
```

##### Manejo de Respuestas Vacías
Si no tienes datos para enviar en la respuesta JSON, simplemente pasa nil como cuerpo:
```go
response.JSON(w, http.StatusNoContent, nil)
```

---

### Error

- **Respuestas de Error Estandarizadas**: Genera respuestas de error JSON con un formato consistente, incluyendo un estado y un mensaje.
- **Flexibilidad en Mensajes de Error**: Permite personalizar el mensaje de error y el código de estado HTTP para adaptarse a diferentes situaciones de error.
- **Función de Formato de Error**: Soporta la creación de mensajes de error formateados, similar a cómo `fmt.Sprintf` maneja los strings.

#### Uso

##### Enviando una Respuesta de Error

Para enviar una respuesta de error estándar, utiliza la función `Error`:

```go
import "github.com/tu_usuario/tu_repositorio/response"

func miHandler(w http.ResponseWriter, r *http.Request) {
    // Algún código que puede generar un error
    if ocurrioUnError {
        response.Error(w, http.StatusBadRequest, "Descripción del error")
        return
    }
}
```

---

### Text

- **Escribir Respuestas de Texto**: Permite escribir respuestas de texto en el cuerpo de una respuesta HTTP con un código de estado específico.
- **Codificación de Caracteres UTF-8**: Codifica automáticamente el texto con caracteres UTF-8 para manejar caracteres especiales correctamente.

#### Uso

##### Escribiendo una Respuesta de Texto

Para enviar una respuesta de texto simple, utiliza la función `Text`:

```go
import "github.com/tu_usuario/tu_repositorio/response"

func miHandler(w http.ResponseWriter, r *http.Request) {
    response.Text(w, http.StatusOK, "Hola mundo")
}
```