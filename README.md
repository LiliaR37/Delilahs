
# Delilah
Proyecto Final - Curso Acámica

PASOS:

1- INSTALACIÓN DE LA APP - Agregar los siguientes comandos para iniciar la app. 

-> npm run install 
-> npm run migrations
-> npm run start

El dominio se hará por medio de:  -> localhost:4444


2- END POINTS


>> AGREGAR USUARIO
    // El role del usuario puede ser ADMIN | USER
    
  Por medio de POST: Rellenar los siguientes datos.. 

    [POST] /user/add
    {
        "USER_NAME": "",
        "FULL_NAME": "",
        "EMAIL": "",
        "PHONE_COUNTRY_CODE": ,
        "PHONE_NUMBER": ,
        "ADDRESS": "",
        "PASSWORD": "",
        "ROLE": "" 
    }

    [RESPUESTA] 
    {
        "fieldCount": 0,
        "affectedRows": 1,
        "insertId": 15,
        "info": "",
        "serverStatus": 2,
        "warningStatus": 0
    }

>> LOGIN (usuario)
 
 Por medio de POST: Rellenar los siguientes datos y como respuesta  se obtendrá  el "Token". 
 
    [POST] /user/login
    {
        "USER_NAME": "",
        "EMAIL": "",
        "PASSWORD": ""
    }

    [RESPUESTA]
    {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTUsIlVTRVJfTkFNRSI6ImFzZHNhIiwiRU1BSUwiOiJkc2Fkc2EiLCJST0xFIjoiQURNSU4iLCJpYXQiOjE2MDA5OTMwNzB9.PomyN_NdYIdbdFuWhGtetopD8TGiyeoUV18GF08uDTg"
    }

>> OBTENER EL LISTADO DE PRODUCTOS 

 Por medio de GET: 

    [GET] /productos

    [RESPUESTA] 
    [
        {
            "ID": 1,
            "PRODUCT_NAME": "Hamburguesa",
            "PRODUCT_PRICE": 100,
            "PRODUCT_IMAGE": "https://www.ipcc.ch/site/assets/uploads/sites/3/2019/10/img-placeholder.png"
        }
    ]

>> AGREGAR UN NUEVO PRODUCTO
 Por medio de POST: 
 
    [POST] /productos/add
    {
        "PRODUCT_NAME": "Papas", 
        "PRODUCT_PRICE": 100, 
        "PRODUCT_IMAGE": "https://.jpg",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTUsIlVTRVJfTkFNRSI6ImFzZHNhIiwiRU1BSUwiOiJkc2Fkc2EiLCJST0xFIjoiQURNSU4iLCJpYXQiOjE2MDA5OTMwNzB9.PomyN_NdYIdbdFuWhGtetopD8TGiyeoUV18GF08uDTg"
    }

    [RESPUESTA]
    {
        "fieldCount": 0,
        "affectedRows": 1,
        "insertId": 7,
        "info": "",
        "serverStatus": 2,
        "warningStatus": 0
    }

>> REMOVER PRODUCTO
 Por medio de POST: 

    [POST] /productos/remove
    {
        "PRODUCT_NAME" : "apple", 
        "PRODUCT_PRICE" : 900, 
        "PRODUCT_IMAGE" :"https:/img.jps",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTUsIlVTRVJfTkFNRSI6ImFzZHNhIiwiRU1BSUwiOiJkc2Fkc2EiLCJST0xFIjoiQURNSU4iLCJpYXQiOjE2MDA5OTMwNzB9.PomyN_NdYIdbdFuWhGtetopD8TGiyeoUV18GF08uDTg"
    }

    [RESPUESTA]
    {
        "fieldCount": 0,
        "affectedRows": 1,
        "insertId": 0,
        "info": "",
        "serverStatus": 34,
        "warningStatus": 0
    }

>> ACTUALIZAR DATOS DE UN PRODUCTO
 Por medio de POST: 

    [POST] /productos/update
    {
        "PRODUCT_NAME" : <valor_a_actualizar>, 
        "PRODUCT_PRICE" : <valor_a_actualizar>, 
        "PRODUCT_IMAGE" : <valor_a_actualizar>
        "WHERE" : {
            "ID" : <condicion>,
            "PRODUCT_NAME" : <condicion>, 
            "PRODUCT_PRICE" : <condicion>, 
            "PRODUCT_IMAGE" : <condicion>
        }
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTUsIlVTRVJfTkFNRSI6ImFzZHNhIiwiRU1BSUwiOiJkc2Fkc2EiLCJST0xFIjoiQURNSU4iLCJpYXQiOjE2MDA5OTMwNzB9.PomyN_NdYIdbdFuWhGtetopD8TGiyeoUV18GF08uDTg"
    }

    [RESPUESTA]
    {
        "fieldCount": 0,
        "affectedRows": 1,
        "insertId": 0,
        "info": "",
        "serverStatus": 34,
        "warningStatus": 0
    }

>> OBTENER UN PEDIDO

    //Los ADMINS son los que pueden ver todos los pedidos.  Los USERS solo poseen  permisos para retornar sus proprios pedidos.
     
     Por medio de GET: 

    [GET] /order?token<>

    [RESPUESTA]
    [
        {
            "ID": 1,
            "ESTADO": "CONFIRMADO",
            "HORA": "21:56",
            "DESCRIPCION": null,
            "PAGO": 1.4,
            "USUARIO": 11,
            "DIRECCION": null
        }
    ]

>> CREAR PEDIDO

 Por medio de POST: 

    [POST] /order/create
    {
        "PAGO": "11",
        "DIRECCION": "Direccion",
        "PRODUCTOS": {
            <id_del_producto> : {
                "QNT": <cantidad_de_unidades>
            },
            <id_del_producto> : {
                "QNT": <cantidad_de_unidades>
            }
        },
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTUsIlVTRVJfTkFNRSI6ImFzZHNhIiwiRU1BSUwiOiJkc2Fkc2EiLCJST0xFIjoiQURNSU4iLCJpYXQiOjE2MDA5OTMwNzB9.PomyN_NdYIdbdFuWhGtetopD8TGiyeoUV18GF08uDTg"
    }

>> EDITAR UN PEDIDO

    //Los pedidos aceptan los estados ('NUEVO', 'CONFIRMADO', 'PREPARANDO', 'ENVIANDO', 'CANCELADO', 'ENTREGADO')
    
     Por medio de POST: 

    [POST] /order/edit
    {	
	    "ESTADO" : "CONFIRMADO",
        "DESCRIPCION" : "DESCRIPCION",
        "DIRECCION" : "DIRECCION", 
        "WHERE": {
		    "ID" : "1"
	    },
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTQsIlVTRVJfTkFNRSI6IlVTRVJURVNUVFQiLCJFTUFJTCI6IlVTRVJURVNUQFVTRVJURVNULlVTRVJVU0VSVEVTVFRUVEVTVCIsIlJPTEUiOiJBRE1JTiIsImlhdCI6MTYwMDgxOTMxOH0.lS481Xro9oZ24mK2KtpEorNpydcBAqK1WXi7uCdmCRc"
    }

>> BORRAR UN PEDIDO 
 	
	Por medio de POST:

    [POST] /order/delete
    {
        ID: <numero>,
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJJRCI6MTQsIlVTRVJfTkFNRSI6IlVTRVJURVNUVFQiLCJFTUFJTCI6IlVTRVJURVNUQFVTRVJURVNULlVTRVJVU0VSVEVTVFRUVEVTVCIsIlJPTEUiOiJBRE1JTiIsImlhdCI6MTYwMDgxOTMxOH0.lS481Xro9oZ24mK2KtpEorNpydcBAqK1WXi7uCdmCRc"
    }


