# FacturaProducto
## listarTipoComprobante

>Lista los tipos de comprobante con su id

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/listarTipoComprobante

**Method** : `GET`

Headers

```json
noHeaders
```

Body

```json
noBody
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien y se registró la factura.

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": [
    {
      "id": 1,
      "nombre": "factura"
    },
    {
      "id": 2,
      "nombre": "remision"
    }
  ],
  "message": "Petición realizada exitosamente"
}
```

#### Respuesta de error

**Condición** : no se encontraron datos

**Codigo**: `400 Bad Request`

**Contenido** : 
```json
{
  "code": 22,
  "data": [],
  "message": "No se encontraron datos de la factura"
}
```


## insertar

>Crea un registro nuevo de facturaProducto

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/insertar`

**Method** : `POST`

Headers

```json
{
    "proveedor_id": "[entero]",
    "tipoComprobante_id": "[1 para Factura | 2 para remision]"
}
```

Body

```json
{
    "folio_factura": "MIG-MIE-22-05",
    "fecha_emision": "2024-05-22",
    "meses_garantia": 3,
    "buffer": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAA1JREFUGFdjWGJx5D8ABcQCoNLRvt8AAAAASUVORK5CYII="
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

## agregarComprobanteFactura

>Registra un comprobante de factura para una factura que no tenga.

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/agregarComprobanteFactura`

**Method** : `PUT`

Headers

```json
{
    "factura_id": "[ID][NUMERO][ENTERO]"
}
```

Body

```json
{
    "buffer": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAA1JREFUGFdjWGJx5D8ABcQCoNLRvt8AAAAASUVORK5CYII="
}
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien y se registró el comprobante para factura.

**Code** : `200 OK`

**Contenido**

```json
{
    "code": 0,
    "data": [],
    "message": "comprobante de factura insertado correctamente"
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
  "message": "Solo se permiten documentos PDF como comporobante de factura"
}
```

## actualizarComprobanteFactura

>Borra el comprobante anterior de factura y registra uno nuevo

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/actualizarComprobanteFactura`

**Method** : `PUT`

Headers

```json
{
    "factura_id": "[ID][NUMERO][ENTERO]"
}
```

Body

```json
{
    "buffer": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAA1JREFUGFdjWGJx5D8ABcQCoNLRvt8AAAAASUVORK5CYII="
}
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien y se registró el comprobante para factura.

**Code** : `200 OK`

**Contenido**

```json
{
    "code": 0,
    "data": [],
    "message": "comprobante de factura insertado correctamente"
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
  "message": "Solo se permiten documentos PDF como comporobante de factura"
}
```

## cambiarRemisionAFactura

> Actualiza un registro de remisión como factura con su comprobante.

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/cambiarRemisionAFactura`

**Method** : `PUT`

Headers

```json
{
    "factura_id": "[ID][NUMERO][ENTERO]"
}
```

Body

```json
{
    "buffer": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAA1JREFUGFdjWGJx5D8ABcQCoNLRvt8AAAAASUVORK5CYII="
}
```

#### Respuesta Exitosa

**Condición** : Si todo salió bien y se registró el comprobante para factura.

**Code** : `200 OK`

**Contenido**

```json
{
    "code": 0,
    "data": [],
    "message": "remisión actualizada a factura correctamente"
}
```

#### Respuesta de error

**Condición** : Si ya existe un registro de factura con ese id de proveedor y folio_factura

**Código**: `400 Bad Request`

**Contenido** : 
```json
{
  "code": 22,
  "data": "error",
  "message": "Solo se permiten documentos PDF como comporobante de factura"
}
```

## listar

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
      "proveedor": "grupoGonz",
      "folio_factura": "MIG-MIE-22-05",
      "meses_garantia": 3,
      "tipocomprobante_id": 1,
      "tipocomprobante": "factura",
      "fecha_emision": "2024-05-22 00:00:00",
      "fecha_actualizacion": "2024-05-22 00:00:00",
      "ruta_factura": "Facturas/MIG-MIE-22-05.pdf"
    },
    {
      "id": 2,
      "proveedor_id": 1,
      "proveedor": "grupoGonz",
      "folio_factura": "MIG-MIE-24-05",
      "meses_garantia": 6,
      "tipocomprobante_id": 1,
      "tipocomprobante": "factura",
      "fecha_emision": "2024-05-22 00:00:00",
      "fecha_actualizacion": "2024-05-22 00:00:00",
      "ruta_factura": "Facturas/MIG-MIE-24-05.pdf"
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

## detalles

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
    "tipoComprobante_id": 1,
    "tipoComprobante": "factura",
    "folio_factura": "RR-00822",
    "proveedor_id": 10,
    "proveedor": "Ricardo",
    "direccion_proveedor": "aqui morpheus",
    "telefono_proveedor": "1111111111",
    "correo_proveedor": "",
    "meses_garantia": 24,
    "fecha_emision": "2024-04-04 00:00:00",
    "fecha_actualizacion": "2024-04-04 00:00:00",
    "ruta_factura": "Facturas/RR-00822.pdf",
    "detalles": [
      {
        "cantidad": 7,
        "categoria": "Teléfono",
        "movimientoinventario_id": 460546,
        "imei": [
          "200000000100229",
          "200000000100230",
          "200000000100224",
          "200000000100225",
          "200000000100227",
          "200000000100226",
          "200000000100228"
        ],
        "marca": "OPPO",
        "modelo": "R8106",
        "producto_id": 110,
        "codigo": "OPPO",
        "color_id": 111,
        "color": "Verde petróleo",
        "precioFactura": 6397
      },
      {
        "cantidad": 5,
        "categoria": "Teléfono",
        "movimientoinventario_id": 460547,
        "imei": [
          "200000000100235",
          "200000000100234",
          "200000000100233",
          "200000000100232",
          "200000000100231"
        ],
        "marca": "12C 6/128 gb",
        "modelo": "nueva",
        "producto_id": 2710,
        "codigo": "VINICIUS",
        "color_id": 92,
        "color": "Gris Pizarra",
        "precioFactura": 1234
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
## buscarPorImei

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
    "tipoComprobante_id": 1,
    "tipoComprobante": "factura",
    "folio_factura": "RR-00822",
    "proveedor_id": 10,
    "proveedor": "Ricardo",
    "direccion_proveedor": "aqui morpheus",
    "telefono_proveedor": "1111111111",
    "correo_proveedor": "",
    "meses_garantia": 24,
    "fecha_emision": "2024-04-04 00:00:00",
    "fecha_actualizacion": "2024-04-04 00:00:00",
    "ruta_factura": "Facturas/RR-00822.pdf",
    "detalles": [
      {
        "cantidad": 7,
        "categoria": "Teléfono",
        "movimientoinventario_id": 460546,
        "imei": [
          "200000000100229",
          "200000000100230",
          "200000000100224",
          "200000000100225",
          "200000000100227",
          "200000000100226",
          "200000000100228"
        ],
        "marca": "OPPO",
        "modelo": "R8106",
        "producto_id": 110,
        "codigo": "OPPO",
        "color_id": 111,
        "color": "Verde petróleo",
        "precioFactura": 6397
      },
      {
        "cantidad": 5,
        "categoria": "Teléfono",
        "movimientoinventario_id": 460547,
        "imei": [
          "200000000100235",
          "200000000100234",
          "200000000100233",
          "200000000100232",
          "200000000100231"
        ],
        "marca": "12C 6/128 gb",
        "modelo": "nueva",
        "producto_id": 2710,
        "codigo": "VINICIUS",
        "color_id": 92,
        "color": "Gris Pizarra",
        "precioFactura": 1234
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
  "message": "La longitud del campo imei debe ser de 15 caracteres :)"
}
```

## actualizarDetalle

>Busca una factura asociada al imei proporcionado y muestra todos sus detalles.

**URL** : `https://pruebasmorpheus.com:19000/productoFactura/actualizarDetalle

**Method**: `PUT`

**Headers**: 

```json
{
    "factura_id": "[soloNumerosEnteros]",
    "movimientoinventario_id": "[soloNumerosEnteros]"
}
```

**Body**:

```json
{
	cantidad: num,
	color_id: id,
	clave: 1234,
	imei: [
		imei,
		imei,
		imei,
	] //opcional, si no es de tipo telefono no mandar campo imei
}
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
  "code": 0,
  "data": "S/R",
  "message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Si no se recibe un id `

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 21,
  "data": "error",
  "message": "No se encontró factura con el id proporcionado"
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
  "message": "La longitud de los imeis debe ser de 15 caracteres :)"
}
```


# Inventario

## busqueda/imeis

>Busca relacione entre el personal venta e imeis proporcionados

**URL** : `https://pruebasmorpheus.com:19000/inventario/busqueda/imeis

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
## listar/imeifaltante

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
}
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

## insert/imei

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
  "data": {
    "0": "123123123123121",
    "1": "123123123123122"
  },
  "message": "IMEIs insertados exitosamente"
}
```

#### Respuestas de error

**Condición** : `imeis ya registrados en la base de datos`

**Código** : `200 Ok`

**Contenido** : 
```json
{
  "code": 29,
  "data": [
    "El IMEI 123123123123101 pertenece a Personal Almacen",
    "El IMEI 123123123123102 pertenece a Personal Almacen"
  ],
  "message": "IMEI's registrados en BD"
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






## listar/movimientoimei #incompleto

>Lista los productos de un personalventa con la cantidad actual y la cantidad de imeis registrados.

**URL** : `https://pruebasmorpheus.com:19000/producto/listar/movimientoimei

**Method**: `GET`

**Headers**: 

```json
{
    "tipomovimientoinventario_id": "[entero][>0]"
    "personalventa_id": "[entero][>0]"
}
```

**Body**:
```json
{
  "fecha_inicio": "2023-12-01",
  "fecha_final": "2024-01-30"
}
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
//falta
}
```

#### Respuestas de error

**Condición** : `imeis ya registrados en la base de datos`

**Código** : `200 Ok`

**Contenido** : 
```json
{
//falta
}
```

**Condición** : `formato incorrecto de personalventa_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
//falta
}
```

## descuento/inventario

>Descuenta cantidad de inventario de un producto

**URL** : `https://pruebasmorpheus.com:19000/producto/descuento/inventario

**Method**: `PUT`

**Headers**: 

```json
{ 
	inventario_id: 32729, //[entero][>0]
	producto_id: 2671, //[entero][>0]
	personalventa_id: 59, //[entero][>0]
	tipomovimientoinventario_id: 4, //[entero][>0]
	permiso_usuario: "superadministrador" //['normal' || 'administrador' || 'superadministrador']
}
```

**Body**:
```json
{ 
	"cantidad": 1, 
	"clave": 8273, 
	"oldImei": [ 712309865720001 ] 
}
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
	"code": 0,
	"data": [],
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Error en el proceso`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 29,
  "data": ["S/R"],
  "message": "Error peticion obtener movimientos de imeis"
}
```

**Condición** : `formato incorrecto de personalventa_id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
	"code": 23,
	"data": "S/R",
	"message": "Petición obtener personal venta sin resultados"
}
```


## insert/productoAccesorio

>Agrega un accesorio

**URL** : `https://pruebasmorpheus.com:19000/producto/insert/productoAccesorio

**Method**: `POST`

**Headers**: 

```json
noHeaders
```

**Body**:
```json
{
	codigo: "String", 
	categoria: "String", 
	marca: "String", 
	modelo: "String", 
	precioVentaMax: Int,
	precioVentaMin: int,
	precioFactura: Int,
	precioSubdistribuidor: Int, 
	precioMayorista: Int, 
	caracteristica: {
		id: Int,
		decripcion: "String"
	},
	imagen: {
		identificador: ["1/0"], //0 para imagen principal 1 para secundaria
		nombre: "String",
		buffer: "StringBase64"
	}
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
		categoria_id: 1,
		marca_id: 1,
		modelo_id: 1,
		producto_id: 1
	},
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Error en el proceso`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 29,
  "data": ["S/R"],
  "message": "Error de petición"
}
```

**Condición** : `formato incorrecto de caracteristica.id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
	"code": 23,
	"data": "S/R",
	"message": "el campo caracteristica.id debe ser un Entero"
}
```



# Ventas
## rutas

>Registra una venta 

**URL** : `https://pruebasmorpheus.com:19000/ventas/rutas

**Method**: `POST`

**Headers**: 

```json
noHeaders
```

**Body**:
```json
[
  {
    "cliente_id": 99,
    "folio": "21398252",
    "credito": 0,
    "abono": 0,
    "usuario": 1103,
    "key": "1675373466559"
  },
  [
    {
      "producto_id": 29,
      "cantidad": 1,
      "precioFinal": 210,
      "tipoProduct": 1,
      "categoriaProducto": "Teléfono",
      "personalVenta_id": 14,
      "tipo": "Venta",
      "producto_modelo": 29,
      "color_id": 6,
      "inventarioVenta_id": 4973,
      "categoriaProducto_id": 2,
      "imagen": "alcatel_1050L.png",
      "url": "android/VentasMarquesadaV.1.1/imagenes/imagen_productos/",
      "color": "Negro",
      "hexadecimal": "#FF000000",
      "marca": "Alcatel",
      "modelo": "1050A L",
      "tipoTelefono": "0",
      "imei": ["314159265358980", "314159265358980", "314159265358981"]
    },
	{
      "producto_id": 29,
      "cantidad": 1,
      "precioFinal": 210,
      "tipoProducto": 1,
      "categoriaProducto": "Teléfono",
      "personalVenta_id": 14,
      "tipo": "Venta Plan",
      "tipoplan": 2,
      "referencia": "SDKD34938SD",
      "producto_modelo": 29,
      "color_id": 6,
      "inventarioVenta_id": 4973,
      "categoriaProducto_id": 2,
      "imagen": "alcatel_1050L.png",
      "url": "android/VentasMarquesadaV.1.1/imagenes/imagen_productos/",
      "color": "Negro",
      "hexadecimal": "#FF000000",
      "marca": "Alcatel",
      "modelo": "1050A L",
      "tipoTelefono": "0",
      "imei": ["314159265358983", "314159265358982", "314159265358983"]
    }
  ]
]
```

#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`
**Code** : `200 OK`
**Contenido** :
```json
{
	"code": 0,
	"data": [],
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Error en el proceso`
**Código** : `400 Bad Request`
**Contenido** : 
```json
{
  "code": 29,
  "data": ["S/R"],
  "message": "Error de petición"
}
```

**Condición** : `formato incorrecto de caracteristica.id`
**Código** : `400 Bad Request`
**Contenido** :
```json
{
	"code": 23,
	"data": "S/R",
	"message": "el campo caracteristica.id debe ser un Entero"
}
```

## /notificacion/creditoCliente

>Notificacion para solicitar un credito de venta a un cliente

**URL** : `https://pruebasmorpheus.com:19000/notificacion/creditoCliente

**Method**: `POST`

**Headers**: 

```json
{
  cliente_id: [Int],
  personalventa_id: [Int]
}
```

**Body**:
```json
{
  "mensaje": "El monto del crédito es: $13,287.00",
  "titulo": "Se registro un nuevo crédito",
  "tipoUsuario": "Cliente",
  "tipoNotificacion": "VentaCredito",
  "json": [
    {
      "cliente_id": 466,
      "folio": "415332314",
      "credito": 1,
      "abono": 0,
      "usuario": 8,
      "key": "1602878603900"
    },
    [
      {
        "producto_id": 679,
        "cantidad": 3,
        "precioFinal": 4429,
        "tipoProducto": 1,
        "categoriaProducto": "Teléfono",
        "personalVenta_id": 6,
        "tipo": "Venta",
        "producto_modelo": 675,
        "color_id": 44,
        "inventarioVenta_id": 9165,
        "categoriaProducto_id": 2,
        "imagen": "motog7.png",
        "url": "android/VentasMarquesadaV.1.1/imagenes/imagen_productos/",
        "color": "Azul Fuerte",
        "hexadecimal": "#00006C",
        "marca": "MOTOROLA",
        "modelo": "G7 +",
        "tipoTelefono": "0",
        "imei": [
          "183628631085342",
          "852988741072463",
          "989623173624758"
        ]
      }
    ]
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
	"data": [],
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Error en el proceso`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 29,
  "data": ["S/R"],
  "message": "Error de petición"
}
```

**Condición** : `formato incorrecto de caracteristica.id`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
	"code": 23,
	"data": "S/R",
	"message": "el campo caracteristica.id debe ser un Entero"
}
```
# Proveedor
## desactivar
>Desactivar un provedor vinculados a la factura

**URL** : `https://pruebasmorpheus.com:19000/proveedor/desactivar

**Method**: `PUT`

**Headers**: 

```json
{
  proveedor_id: [Int]
}
```
#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
	"code": 0,
	"data": [],
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Error en el proceso`
**Código** : `400 Bad Request`
**Contenido** : 
```json
{
  "code": 29,
  "data": ["S/R"],
  "message": "Error de petición"
}
```

**Condición** : `Error interno del servidor`
**Código** : `500`
**Contenido** :
```json
{
	"data": "S/R",
	"message": "Error interno del servidor"
}
```

## actualizar
>Desactivar un provedor vinculados a la factura

**URL** : `https://pruebasmorpheus.com:19000/proveedor/actualizar

**Method**: `PUT`

**Headers**: 

```json
{
  proveedor_id: [Int]
}
```

**Body**:
```json
{
    "nombre": "S/R",
    "direccion": "S/R",
    "telefono": "6663332266",
    "correo": "S/R"
}
```
#### Respuesta Exitosa

**Condición** : `Si todo salió bien.`

**Code** : `200 OK`

**Contenido**

```json
{
	"code": 0,
	"data": [],
	"message": "Petición realizada exitosamente"
}
```

#### Respuestas de error

**Condición** : `Formato incorrecto en parametros`

**Código** : `400 Bad Request`

**Contenido** : 
```json
{
  "code": 20,
  "data": "error",
  "message": "Parametros incorrectos"
}
```

**Condición** : `Error interno del servidor`

**Código** : `500`

**Contenido** : 
```json
{
  "code": 20,
  "data": "error",
  "message": "Error interno del servidor"
}
