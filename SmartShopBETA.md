# FacturaProducto
## `POST`/productofactura/insertar

>Crea un registro nuevo de facturaProducto

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/insertar`

**Method** : `POST`

Headers

```json
{
    "proveedor_id": "[entero]"
}
```

Body

```json
{
	"folio_factura": "MIG-MIE-22-05",
	"fecha_emision": "2024-05-22",
	"meses_garantia": 3
}
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien y se registró la factura.

**Code** : `200 OK`

**Contenido**

```json
{
	"code": 0,
	"data": "factura insertada correctamente",
	"message": "Petición realizada exitosamente"
}
```

#### Respuesta de error

**Condición** : Si ya existe un registro de factura con ese id de proveedor y folio_factura

**Codigo**: `400 Bad Request`

**Contenido** : 
```json
{
  "code": 22,
  "data": "error",
  "message": "Los Datos de factura ya existen"
}
```
## `GET` /productoFactura/listar

>Lista todos los registros de factura o los de un proveedor

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/listar`

**Method** : `GET`

Headers

```json
{
    "proveedor_id": "[entero] [0:Para listar todo]"
}
```

Body

```json
No Body
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien.

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": [
    {
      "id": 1,
      "proveedor_id": 1,
      "folio_factura": "MIG-MIE-22-05",
      "meses_garantia": 3,
      "fecha_emision": "2024-05-22T06:00:00.000Z"
    },
    {
      "id": 2,
      "proveedor_id": 1,
      "folio_factura": "MIG-MIE-24-05",
      "meses_garantia": 6,
      "fecha_emision": "2024-05-22T06:00:00.000Z"
    }
  ],
  "message": "Petición realizada exitosamente"
}
```

#### Respuesta de error

**Condición** : Si no se recibe un valor valido en proveedor_id

**Codigo**: `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo proveedor_id debe contener solo números"
}
```

## `GET` /productoFactura/detalles

>Lista todos los detalles de los productos de una factura

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/detalles`

**Method**: `GET`

**Headers**: 

```json
{
    "factura_id": "[entero][>0]"
}
```

**Body**:

```json
No Body
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": {
    "folio_factura": "MIG-MIE-22-05",
    "proveedor": "grupoGonz",
    "fecha_emision": "2024-05-22 00:00:00",
    "detalles": [
      {
        "cantidad": 10,
        "imei": [
          "712309865720001",
          " 712309865720002",
          " 712309865720003",
          " 712309865720004",
          " 712309865720005",
          " 712309865720006",
          " 712309865720007",
          " 712309865720008",
          " 712309865720009",
          " 712309865720010"
        ],
        "marca": "Samsung",
        "modelo": "Samsung A54 5G 6/128 GB",
        "color": "Acero",
        "precioFactura": 5000
      }
    ]
  },
  "message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Si no se recibe un valor valido en factura_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo factura_id debe contener solo números"
}
```

**Condición** : `Si no se encontraron datos asociados a esa factura_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 23,
  "data": "S/R",
  "message": "No se encontraron datos de la factura"
}
```
## `GET` /productoFactura/buscarPorImei

>Busca una factura asociada al imei proporcionado y muestra todos sus detalles.

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/buscarPorImei

**Method**: `GET`

**Headers**: 

```json
{
    "imei": "[soloNumeros][longitud=15]"
}
```

**Body**:

```json
No Body
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": {
    "folio_factura": "MIG-MIE-22-05",
    "proveedor": "grupoGonz",
    "fecha_emision": "2024-05-22 00:00:00",
    "detalles": [
      {
        "cantidad": 10,
        "imei": [
          "712309865720001",
          " 712309865720002",
          " 712309865720003",
          " 712309865720004",
          " 712309865720005",
          " 712309865720006",
          " 712309865720007",
          " 712309865720008",
          " 712309865720009",
          " 712309865720010"
        ],
        "marca": "Samsung",
        "modelo": "Samsung A54 5G 6/128 GB",
        "color": "Acero",
        "precioFactura": 5000
      }
    ]
  },
  "message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Si no se recibe un valor valido en imei`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo imei debe contener solo números"
}
```

**Condición** : `Si no se encontraron datos asociados a ese imei`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 23,
  "data": "S/R",
  "message": "No se encontró factura realacionada a ese imei"
}
```

**Condición** : `Longitud incorrecta del campo imei`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "La longitud del campo imei debe ser de 15 caracteres"
}
```
# Inventario
## `GET` /inventario/busqueda/imeis

>Busca una factura asociada al imei proporcionado y muestra todos sus detalles.

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/buscarPorImei

**Method**: `GET`

**Headers**: 

```json
{
    "personalventa_id": "[entero][>0]"
}
```

**Body**:

```json
{
  "imei": [
    "712309865720001",
    "712309865720002",
    "712309865720003",
    "712309865720004",
    "712309865720005",
    "712309865720006",
    "712309865720007",
    "712309865720008",
    "712309865720009",
    "712309865720015"
  ]
}
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": {
    "correctos": [
      {
        "producto_id": 2671,
        "codigo": "IMEIFRONT",
        "color_id": 42,
        "color": "Acero",
        "categoria": "Teléfono",
        "marca": "Samsung",
        "modelo": "Samsung A54 5G 6/128 GB",
        "cantidad": 9,
        "imei": [
          "712309865720001",
          "712309865720002",
          "712309865720003",
          "712309865720004",
          "712309865720005",
          "712309865720006",
          "712309865720007",
          "712309865720008",
          "712309865720009"
        ]
      }
    ],
    "incorrectos": [
      {
        "imei": "712309865720015",
        "mensaje": "Imei no registrado en la base de datos"
      }
    ]
  },
  "message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Si algunos imeis no tienen formato correcto`

**Código** : `200 Ok`

**Contenido** : 
```json
{
  "code": 0,
  "data": {
    "correctos": [
      {
        "producto_id": 2671,
        "codigo": "IMEIFRONT",
        "color_id": 42,
        "color": "Acero",
        "categoria": "Teléfono",
        "marca": "Samsung",
        "modelo": "Samsung A54 5G 6/128 GB",
        "cantidad": 7,
        "imei": [
          "712309865720001",
          "712309865720003",
          "712309865720004",
          "712309865720005",
          "712309865720006",
          "712309865720007",
          "712309865720009"
        ]
      }
    ],
    "incorrectos": [
      {
        "imei": "asd",
        "mensaje": "Imei con valores no permitidos o incorrectos"
      },
      {
        "imei": "azulazulazulazu",
        "mensaje": "Imei con valores no permitidos o incorrectos"
      },
      {
        "imei": "712309865720015",
        "mensaje": "Imei no registrado en la base de datos"
      }
    ]
  },
  "message": "Petición realizada exitosamente"
}
```

**Condición** : `formato incorrecto de personalventa_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo personalventa_id debe contener solo números"
}
```
# Producto
## `GET` /producto/listar/imeifaltante

>Lista los productos de un personalventa con la cantidad actual y la cantidad de imeis registrados.

**URL** : `https://pruebasmorpheus.com:19000/producto/listar/imeifaltante

**Method**: `GET`

**Headers**: 

```json
{
    "personalventa_id": "[entero][>0]"
}
```

**Body**:

```json
No Body
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": [
	  {
      "producto_id": 2569,
      "codigo": "REDMI105G4/64LB",
      "marca": "XIAOMI",
      "modelo": "REDMI 10 5G 4/64 GB",
      "categoria": "Teléfono",
      "color": "PLATA",
      "cantidad": 1,
      "imeis_registrados": 0,
      "imei": null
    },
     {
      "producto_id": 2326,
      "codigo": "MOTOE1364GBLB",
      "marca": "MOTOROLA",
      "modelo": "MOTO E13 2/64GB",
      "categoria": "Teléfono",
      "color": "Blanco",
      "cantidad": 5,
      "imeis_registrados": 2,
      "imei": [
	      "712309865720008",
	      "712309865720009"
      ]
    }
  ],
  "message": "Petición realizada exitosamente"
```

#### Respuestas de error

**Condición** : `el personalventa no tiene productos`

**Código** : `200 Ok`

**Contenido** : 
```json
{
  "code": 23,
  "data": "S/R",
  "message": "Petición obtener personal venta sin resultados"
}
```

**Condición** : `formato incorrecto de personalventa_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo personalventa_id debe contener solo números"
}
```

## `POST` /producto/insert/imei

>Lista los productos de un personalventa con la cantidad actual y la cantidad de imeis registrados.

**URL** : `https://pruebasmorpheus.com:19000/producto/insert/imei

**Method**: `POST`

**Headers**: 

```json
{
    "producto_id": "[entero][>0]"
    "personalventa_id": "[entero][>0]"
}
```

**Body**:
`cantidad debe coincidir con el numero de imeis a insertar`
```json
{
  "color": "Gris",
  "cantidad": 2,
  "imei": [
    "123123123123121",
    "123123123123122"
  ]
}
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": [
	  {
      "producto_id": 2569,
      "codigo": "REDMI105G4/64LB",
      "marca": "XIAOMI",
      "modelo": "REDMI 10 5G 4/64 GB",
      "categoria": "Teléfono",
      "color": "PLATA",
      "cantidad": 1,
      "imeis_registrados": 0,
      "imei": null
    },
     {
      "producto_id": 2326,
      "codigo": "MOTOE1364GBLB",
      "marca": "MOTOROLA",
      "modelo": "MOTO E13 2/64GB",
      "categoria": "Teléfono",
      "color": "Blanco",
      "cantidad": 5,
      "imeis_registrados": 2,
      "imei": [
	      "712309865720008",
	      "712309865720009"
      ]
    },
    {...},
    ...
  ],
  "message": "Petición realizada exitosamente"
```

#### Respuestas de error

**Condición** : `el personalventa no tiene productos`

**Código** : `200 Ok`

**Contenido** : 
```json
{
  "code": 23,
  "data": "S/R",
  "message": "Petición obtener personal venta sin resultados"
}
```

**Condición** : `formato incorrecto de personalventa_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "El campo personalventa_id debe contener solo números"
}
```
