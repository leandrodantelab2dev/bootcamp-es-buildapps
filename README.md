# Proyecto SAP Build Apps - Órdenes de Mantenimiento

Este repositorio contiene la documentación, scripts e instrucciones de configuración para dos aplicaciones desarrolladas con **SAP Build Apps**, integradas con **SAP S/4HANA Cloud**.

## 📱 Aplicaciones

### 1. Órdenes de Mantenimiento - Build Apps + S/4HANA Cloud
Aplicación para la gestión de Órdenes de Mantenimiento integrada directamente con **S/4HANA Cloud**.

- **API Utilizada:** [Maintenance Order - Read, Create, Update (A2X)](https://api.sap.com/api/CE_API_MAINTENANCEORDER_0002/overview)  
- **Configuración necesaria:**
  - Crear una **Destination** en SAP BTP apuntando a la API
  - Definir la variable `API_KEY` en el Destination
  - Seguir el paso a paso del video de implementación (enlace será añadido aquí)

> ℹ️ Solo es necesario reemplazar la `apikey` del Destination y seguir las instrucciones.

---

### 2. Órdenes de Mantenimiento - Inteligente
Versión inteligente de la app de mantenimiento, con automatizaciones y lógica adicional.  

Fórmula de conversión de imágenes:
```
"data:image/png;base64," + outputs["Convert file to base64"].base64
```

Url de la solicitud ChatGPT:
```
https://api.openai.com/v1/chat/completions
```

Headers de la solicitud ChatGPT(Key y Value):
```
Content-Type
application/json

Authorization
Bearer [APIKEY EN GRUPO DE WHATSAPP]
```

Payload de la solicitud ChatGPT:
```
{  "model": "gpt-4.1",  "messages": [    {      "role": "user",      "content": [        {          "type": "image_url",          "image_url": {            "url": appVars.ImgBase64      }        },        {          "type": "text",          "text": "Describe brevemente qué es el objeto de la imagen e identifica problemas o defectos en el objeto sin decir 'el objeto de la imagen...', ve directamente a la descripción y al problema o defecto."  }      ]    }  ],  "max_tokens": 1000}
```

Fórmula para obtener el resultado de ChatGPT:
```
STRING(outputs["HTTP request"].resBodyParsed.choices[0].message.content)
```

---

## 🛠 Estructura del Repositorio
```
├── apps/
│   ├── mantenimiento-build/        # App integrado con S/4HANA
│   ├── mantenimiento-inteligente/  # App inteligente con automatizaciones
├── destination/                    # Destination para S/4HANA
├── scripts/                        # Scripts adicionales
│   └── inteligente/                # Scripts para la versión inteligente
└── README.md                       # Este archivo
```

---


## 📚 Referencias
- [SAP Build Apps - Documentación Oficial](https://help.sap.com/docs/build-apps)
- [SAP S/4HANA Cloud APIs](https://api.sap.com)

---

## ✨ Contribución
Este repositorio será actualizado con:
- Documentación detallada
- Scripts listos para usar
- Ejemplos de integración con **BTP**

Las contribuciones y mejoras son bienvenidas a través de **Pull Requests**.
