

<img src="https://ciudadesabiertas.es/assets/img/cabiertas/logo.svg" alt="LogoCiudadesAbiertas" width="200"/> 

# DESARROLLO API REST DE DATOS REUTILIZABLE. MODELO DE TABLAS: 	DEUDA PÚBLICA FINANCIERA

&nbsp;

## **ÍNDICE**   
1. [AUTORES](#id1)
2. [LINKS](#id2)
3. [DIAGRAMA CONCEPTUAL](#id3)
4. [DIAGRAMA ENTIDAD RELACIÓN DE LAS TABLAS](#id40)
5. [TABLAS](#id4)  
    - [DEUDA_F_ANUAL](#id5)  
    - [DEUDA_F_INST_FINANCIACION](#id6)  
    - [DEUDA_F_PRESTAMO](#id7)  
    - [DEUDA_F_REL_PRESTAMO_ENTIDAD](#id8) 
    - [DEUDA_F_EMISION](#id9) 
    - [DEUDA_F_AMORTIZACION](#id10)  
    - [DEUDA_F_CAPITAL_VIVO](#id11) 
    - [DEUDA_F_CARGA_FINANCIERA](#id12)  
    - [DEUDA_ORGANIZATION](#id13) 
6. [TAXONOMÍAS SKOS](#id14)
    - [TIPO-ENTIDAD-PRESTAMISTA](#id15)  
    - [TIPO-PRESTAMO](#id16)    



&nbsp;

## AUTORES <a name="id1"></a>
- Carlos Martínez de la Casa García
- Edna Ruckhaus
- Leticia Rubalcaba
- Oscar Corcho

&nbsp;

## LINKS <a name="id2"></a>


Este documento contiene la información detallada del modelo de datos asociado al vocabulario de los convenios. A continuación, se detallan los enlaces de interés asociados a este vocabulario:

- *[Documentación](http://ciudadesabiertas.es/vocab-economia-deuda-financiera/OnToology/ontology/deudaPublicaFinanciera.owl/documentation/index-es.html)*
- *[Repositorio](https://github.com/CiudadesAbiertas/vocab-economia-deuda-financiera)*
- *[Requisitos](https://github.com/CiudadesAbiertas/vocab-economia-deuda-financiera/blob/master/requirements/Requisitos%20y%20Glosario%20Deuda%20Publica.xlsx)*
- *[Issues](https://github.com/CiudadesAbiertas/vocab-economia-deuda-financiera/issues)*
<!--   - *[Webinar](https://www.youtube.com/watch?v=RcP9dplKb3A&list=PLuvmjKgQP8bXSFG289dUU4I6hOQZhjxUW)*  -->


&nbsp;

## DIAGRAMA CONCEPTUAL <a name="id3"></a>
&nbsp;

El diagrama muestra las clases y propiedades del vocabulario que representa la Deuda Pública Financiera como indicador esencial de las cuentas públicas de un ayuntamiento.

&nbsp;
![Diagrama conceptual](http://ciudadesabiertas.es/vocab-economia-deuda-financiera/OnToology/ontology/deudaPublicaFinanciera.owl/documentation/resources/images/modeloConceptual.png)
&nbsp;



## DIAGRAMA ENTIDAD RELACIÓN DE LAS TABLAS <a name="id40"></a>

&nbsp;
![Diagrama Entidad Relación](Relational Model/DIAGRAMA ENTIDAD RELACIÓN DE LAS TABLAS.png)
&nbsp;






## TABLAS <a name="id4"></a>
En principio se considera esta estructura de datos bastante estable y no se estima que sufrirá cambios. Pero puesto que la actuación D2, que es donde se enmarca la definición de estas tablas, aún está en desarrollo, no se puede asegurar al 100% que será la definitiva.     

[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### DEUDA_F_ANUAL <a name="id5"></a>
&nbsp;

|     Campo               |     Tipo    |                      |     Ejemplo                  |     Descripción                                                                                                                                                                                                                                      |     URL                                                                                                      |
|-------------------------|-------------|----------------------|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     ikey                |             |     VARCHAR(50)      |     DEUDAPBINT01             |     Identificador de la Tabla (PK).                                                                                                                                                                                                                  |                                                                                                              |
|     id                  |             |     VARCHAR(50)      |     2019-cuarto-trimestre    |     Identificador de la deuda pública.                                                                                                                                                                                                               |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     date                |             |     DATETIME         |     2020-03-31 23:00:00.0    |     Un instante de tiempo o período de tiempo.                                                                                                                                                                                                       |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/date          |
|     endeudamientoPDE    |             |     DECIMAL(12,2)    |     51831754.13              |     La deuda elaborada según la metodología del Protocolo de   Deficit Excesivo (PDE), conforme a las definiciones del Sistema Europeo de   Cuentas SEC 2010, es la deuda homogénea y comparable con el resto de las   administraciones públicas.    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#endeudamientoPDE                  |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### DEUDA_F_INST_FINANCIACION <a name="id6"></a>
&nbsp;

|     Campo               |     Tipo             |     Ejemplo                                                                                                                          |     Descripción                                                                                                                                                                                             |     URL                                                                                                         |
|-------------------------|----------------------|--------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
|     ikey                |     VARCHAR(50)      |     1                                                                                                                                |     Identificador de la Tabla (PK).                                                                                                                                                                         |                                                                                                                 |
|     id                  |     VARCHAR(50)      |     ES1234567893                                                                                                                     |     Identificador del instrumento de financiación.                                                                                                                                                          |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier       |
|     importe             |     DECIMAL(12,2)    |     102000000.00                                                                                                                     |     Importe que se financiará con el instrumento.                                                                                                                                                           |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#importe                              |
|     tipo_interes        |     VARCHAR(100)     |     variable                                                                                                                         |     Tipo de tasa   interés (fijo o variable) de un instrumento de financiación                                                                                                                              |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#tipoInteres                          |
|     tasa_fija           |     DECIMAL(12,2)    |     10.95                                                                                                                            |     Porcentaje de interés fijo de un instrumento de financiación                                                                                                                                            |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#tasaFija                             |
|     referencia          |     VARCHAR(100)     |     Euribor 1/3/6 meses                                                                                                              |     Tipo de interés de referencia que puede variar en el tiempo.                                                                                                                                            |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#referencia                           |
|     margen              |     DECIMAL(5,3)     |     0.015                                                                                                                            |     Diferencial aplicable a un interés de tipo variable.                                                                                                                                                    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#margen                               |
|     tipo_instrumento    |     VARCHAR(50)      |     Prestamo                                                                                                                         |     Denota el tipo de instrumento de financiación. Puede tomar los   valores "Prestamo" o "Emision".                                                                                                        |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#tipoInstrumento                      |
|     prestamo            |     VARCHAR(50)      |     es1234567893     URI:   http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica/prestamos/ES1234567893               |     Si el tipo de instrumento es   "Prestamo" relaciona al instrumento de financiación con los datos   en la tabla deuda_f_prestamo.     FK a la tabla deuda_f_prestamo   (identificador del préstamo).     |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#esPrestamo                           |
|     emision             |     VARCHAR(50)      |     es0201001148     URI: http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica/emision/   es0201001148                |     Si el tipo de instrumento es   "Emision" relaciona al instrumento de financiación con los datos en   la clase Emision.           FK a la tabla deuda_f_emision (codISIN)                                |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#esEmision                            |
|     deuda_anual         |     VARCHAR(50)      |     2019-cuarto-trimestre     URI: http://vocab.ciudadesabiertas.es/recurso/economia/deuda-financiera/deuda/2019-cuarto-trimestre    |     Relaciona el instrumento de financiación   con la deuda anual calculada a determinada fecha.           FK a la tabla de deuda_f_anual (identificador   de la deuda)                                     |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#deudaAnualInstrumentoFinanciacion    |


[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### DEUDA_F_PRESTAMO <a name="id7"></a>
&nbsp;


|     Campo                        |     Tipo            |     Ejemplo                                                                                                                           |     Descripción                                                                                                                                                                                                                                                                          |     URL                                                                                                      |
|----------------------------------|---------------------|---------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     ikey                         |     VARCHAR(50)     |     1                                                                                                                                 |     Identificador de la Tabla (PK)                                                                                                                                                                                                                                                       |                                                                                                              |
|     id                           |     VARCHAR(50)     |     ES1234567893                                                                                                                      |     Identificador del préstamo                                                                                                                                                                                                                                                           |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     moneda                       |     VARCHAR(100)    |     euro                                                                                                                              |     Moneda en la cual se realiza un préstamo.                                                                                                                                                                                                                                            |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#moneda                            |
|     fecha_formalizacion          |     DATETIME        |     2020-03-31                                                                                                                        |     Fecha en la cual se suscribe un préstamo.                                                                                                                                                                                                                                            |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#fechaFormalizacion                |
|     plazo                        |     VARCHAR(100)    |     Ejemplo de un período de duración de 16 años:     P16Y     "P16Y"^^xsd:duration ;                                                 |     Lapso de pago de un préstamo.                                                                                                                                                                                                                                                        |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#plazo                             |
|     fecha_inicio                 |     DATETIME        |     2020-01-31                                                                                                                        |     Fecha en que comienzan a devengarse las obligaciones   contraídas en el préstamo.                                                                                                                                                                                                    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#fechaInicio                       |
|     fecha_vencimiento            |     DATETIME        |     2020-03-31                                                                                                                        |     Fecha pactada para devolver el capital prestado.                                                                                                                                                                                                                                     |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#fechaVencimiento                  |
|     diferidas_o_parciales_cap    |     BIT             |     0 (0 – falso, 1 – verdadero)                                                                                                      |     Préstamo con disposiciones diferidas o parciales de capital.                                                                                                                                                                                                                         |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#diferidasOParcialesCapital        |
|     tipo_prestamo                |     VARCHAR(100)    |     Bilateral     Ejemplo de URI:      http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica/tipo-prestamo/bilateral    |     Es el tipo de préstamo según la aplicación CLIR para   operaciones financieras informadas de la Secretaría general de Financiación   Autonómica y Local del Ministerio de Hacienda.     SKOS:   http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica/tipo-prestamo    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#tipoPrestamo                      |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### DEUDA_F_REL_PRESTAMO_ENTIDAD <a name="id8"></a>
&nbsp;

|     Campo                  |     Tipo           |     Ejemplo                                                                                                                                |     Descripción                                                                                  |     URL                                                                                                      |
|----------------------------|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     ikey                   |     VARCHAR(50)    |     1                                                                                                                                      |     Identificador de la Tabla (PK)                                                               |                                                                                                              |
|     id                     |     VARCHAR(50)    |     REL0001                                                                                                                                |     Identificador de la relación                                                                 |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     prestamo_id            |     VARCHAR(50)    |     ES1234567893                                                                                                                           |     Identificador del préstamo     FK a la tabla deuda_f_prestamo      (id de préstamo)          |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     entidad_prestamista    |     VARCHAR(50)    |     q2876002c     Ejemplo de URI:      http://vocab.ciudadesabiertas.es/recurso/economia/deuda-financiera/entidad-prestamista/q2876002c    |     Entidad que otorga el préstamo.     FK a la tabla deuda_organization (id de organización)    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#entidadPrestamista                |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 
&nbsp;
### DEUDA_F_EMISION <a name="id9"></a>
&nbsp;

|     Campo                 |     Tipo             |     Ejemplo                                                  |     Descripción                                                                                                                                                                                                              |     URL                                                                                                      |
|---------------------------|----------------------|--------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     ikey                  |     VARCHAR(50)      |     1                                                        |     Identificador de la Tabla (PK)                                                                                                                                                                                           |                                                                                                              |
|     id                    |     VARCHAR(50)      |     ES0201001148                                             |     Identificador de la Emisión                                                                                                                                                                                              |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     codISIN               |     VARCHAR(50)      |     ES0201001148                                             |     El código ISIN (International Securities Identification Number)   está desarrollado en el estándar internacional ISO 6166 Es un código que   identifica unívocamente un instrumento financiero a nivel internacional.    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#codISIN                           |
|     numero_titulos        |     INT(10)          |     3000                                                     |     Número de títulos emitidos al portador.                                                                                                                                                                                  |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#numeroTitulos                     |
|     cuantia_por_titulo    |     DECIMAL(12,2)    |     100000.00                                                |     Cuantía nominal por título.                                                                                                                                                                                              |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#cuantiaPorTitulo                  |
|     importe_anual         |     DECIMAL(12,2)    |     100000.00                                                |     Importe de cupón bruto anual.                                                                                                                                                                                            |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#importeAnual                      |
|     mes_dia_pago          |     VARCHAR(100)     |     06-16     esdeufin:mesDiaPago "06-16"^^xsd:gMonthDay;    |     Mes y día de pago del importe anual, cada año.                                                                                                                                                                           |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#mesDiaPago                        |
|     precio_emision        |     DECIMAL(12,2)    |     99.81                                                    |     Precio de emisión del título. Es un porcentaje del valor   nominal, es decir de la cuantía por título.                                                                                                                   |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#precioEmision                     |
|     precio_reembolso      |     DECIMAL(12,2)    |     100.00                                                   |     Precio de reembolso de la emisión. Es un porcentaje del valor   nominal, es decir de la cuantía por título.                                                                                                              |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#precioReembolso                   |
|     duracion              |     VARCHAR(100)     |     P30Y     esdeufin:duracion "P30Y"^^xsd:duration ;        |     Tiempo de duración de la emisión.                                                                                                                                                                                        |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#duracion                          |
|     fecha_emision         |     DATETIME         |     2020-03-31                                               |     Fecha en la que se realiza la emisión de los títulos.                                                                                                                                                                    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#fechaEmision                      |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### DEUDA_F_AMORTIZACION <a name="id10"></a>
&nbsp;


|     Campo                       |     Tipo             |     Ejemplo                                                                                                                                          |     Descripción                                                                                                                                                             |     URL                                                                                                               |
|---------------------------------|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
|     ikey                        |     VARCHAR(50)      |     1                                                                                                                                                |     Identificador de la Tabla (PK)                                                                                                                                          |     ikey                                                                                                              |
|     id                          |     VARCHAR(50)      |     es1234567893-c2                                                                                                                                  |     Identificador de la amortización.                                                                                                                                       |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier             |
|     date                        |     DATETIME         |     2019-12-14                                                                                                                                       |     Fecha de amortización que se recoge en el contrato firmado por   ambas partes.                                                                                          |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/date                   |
|     importe                     |     DECIMAL(12,2)    |     39000000.00                                                                                                                                      |     Representa para una fecha dada el importe de amortización de   la deuda que se recoge en el contrato firmado entre las partes.                                          | http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#importe                                        |
|     instrumenta_financiacion    |     VARCHAR(50)      |     es1234567894     Ejemplo de URI: http://vocab.ciudadesabiertas.es/recurso/economia/deuda-financiera/instrumentoFinaciacion/es1234567894          |     Relaciona una amortización con el instrumento de financiación   correspondiente     FK a la tabla de deuda_f_inst_financiacion (identificador del instrumento)          |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#instrumentoFinanciacionPlanAmortizacion    |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### DEUDA_F_CAPITAL_VIVO <a name="id10"></a>
&nbsp;

|     Campo                       |     Tipo             |     Ejemplo                                                                                                                           |     Descripción                                                                                                                                                                                                     |     URL                                                                                                          |
|---------------------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
|     ikey                        |     VARCHAR(50)      |     1                                                                                                                                 |     Identificador de la Tabla (PK)                                                                                                                                                                                  |                                                                                                                  |
|     id                          |     VARCHAR(50)      |     2020-06-30-es1234567893                                                                                                           |     Identificador del capital vivo                                                                                                                                                                                  |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier        |
|     date                        |     DATETIME         |     2019-12-14                                                                                                                        |     Fecha en la que se calcula el capital vivo de un instrumento   de financiación                                                                                                                                  |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/date              |
|     importe                     |     DECIMAL(12,2)    |     39000000.00                                                                                                                       |     Importe del instrumento de financiación pendiente por   amortizar                                                                                                                                               |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#importe                               |
|     instrumenta_financiacion    |     VARCHAR(50)      |     es1234567894     URI: <http://vocab.ciudadesabiertas.es/recurso/economia/deuda-financiera/instrumentoFinaciacion/es1234567894>    |     Relaciona el el importe pendiente de amortizar en una fecha   determinada con su correspondiente instrumento de financiación.     FK a la tabla de deuda_f_inst_financiacion (identificador del isntrumento)    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#instrumentoFinanciacionCapitalVivo    |


[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### AUTOBUS_JOURNEYPATTERN <a name="id11"></a>
&nbsp;

|     Campo                      |     Tipo            |     Ejemplo                                 |     Descripción                                                                                                  |     URL                                                                              |
|--------------------------------|---------------------|---------------------------------------------|------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
|     ikey                       |     VARCHAR(50)     |     BUSJOUPAT01                             |     Identificador de la Tabla (PK).                                                                              |                                                                                      |
|     id                         |     VARCHAR(50)     |     138a2                                   |                                                                                                                  |     http://purl.org/dc/terms/identifier                                              |
|     title                      |     VARCHAR(200)    |     138a2                                   |     Nombre o título.                                                                                             |     http://purl.org/dc/terms/title                                                   |
|     distance                   |     DOUBLE          |     11,194                                  |     Distancia total para una Línea o una Ruta o similares.                                                       |     *[http://w3id.org/transmodel/journeys#distance](http://vocab.ciudadesabiertas.es/def/transporte/autobus/index-es.html#:~:text=boolean-,Distancia,-dp)*                                      |
|     on                         |     VARCHAR(50)     |     138a                                    |     Esta propiedad conecta el patrón de viaje con la ruta en la que   trabaja.                                   |      *[http://w3id.org/transmodel/journeys#on](http://vocab.ciudadesabiertas.es/def/transporte/autobus/index-es.html#:~:text=postal%20c-,en,-op)*                                           |
|     generado_por_incidencia    |     VARCHAR(50)     |     29059944-382A-49AA-A068-B55BF2FAC51F    |     Relación de un patrón de viaje de una ruta que se ha creado por   una incidencia.                            |     http://vocab.ciudadesabiertas.es/def/transporte/autobus#generadoPorIncidencia    |
|     front_text                 |     VARCHAR(50)     |     San Ignacio de Loyola                   |     Texto que se muestra normalmente en la parte frontal de un   vehículo del servicio público de transporte.    |     [http://w3id.org/transmodel/journeys#frontText]*(http://vocab.ciudadesabiertas.es/def/transporte/autobus/index-es.html#:~:text=string-,Letrero%20de%20Cabecera,-dp)*                                    |



[comment]: <!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!> 

&nbsp;
### DEUDA_F_CARGA_FINANCIERA <a name="id12"></a>
&nbsp;

|     Campo                       |     Tipo             |     Ejemplo                                                                                                                           |     Descripción                                                                                                                                                                                  |     URL                                                                                                              |
|---------------------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
|     ikey                        |     VARCHAR(50)      |     1                                                                                                                                 |     Identificador de la Tabla (PK)                                                                                                                                                               |                                                                                                                      |
|     id                          |     VARCHAR(50)      |     2020-06-30-es1234567893                                                                                                           |     Identificador de la carga financiera.                                                                                                                                                        |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier            |
|     anio_fiscal                 |     VARCHAR(4)       |     2017     espresup:anioFiscal "2017"^xsd:gYear ;                                                                                   |     Ejercicio fiscal. Período de 12 meses entre el 1 de enero y 31   de diciembre.                                                                                                               |     http://vocab.ciudadesabiertas.es/def/hacienda/presupuesto#anioFiscal                                             |
|     gasto_o_pasivo              |     VARCHAR(100)     |     gasto financiero                                                                                                                  |     La carga financiera de un instrumento financiero puede   corresponder a un pasivo financiero o a un gasto financiero. Puede tomar los   valores “gasto financiero” y “activo financiero”.    |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#gastoOPasivo                              |
|     description                 |     VARCHAR(400)     |     AMORT.VTO.21/06/17 PTM L/P MDEC-I.C.O.(20,77MM)'06 (2017)                                                                         |     Descripción del gasto financiero o pasivo financiero.                                                                                                                                        |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/description           |
|     date                        |     DATETIME         |     2019-12-14                                                                                                                        |     Fecha en la cual se efectuó el gasto financiero o pasivo   financiero.                                                                                                                       |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/date                  |
|     importe                     |     DECIMAL(12,2)    |     692332.00                                                                                                                         |     Representa el importe del gasto financiero o el pasivo   financiero                                                                                                                          |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#importe                                   |
|     instrumenta_financiacion    |     VARCHAR(50)      |     es1234567894     URI: <http://vocab.ciudadesabiertas.es/recurso/economia/deuda-financiera/instrumentoFinaciacion/es1234567894>    |     FK a la tabla de deuda_f_inst_financiacion                                                                                                                                                   |     http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#instrumentoFinanciacionCargaFinanciera    |


&nbsp;
### DEUDA_ORGANIZATION <a name="id13"></a>
&nbsp;
Esta tabla sigue el estándar de campos que tienen para representar las organizaciones en otros vocbularios. Por lo tanto, no tienen una correspondencia con las propiedades específicas de este vocabulario excepto el campo classification que refiere a una clasificación de tipo de entidad prestamista. 

Nota: misma tabla que se está utilizando en Deuda Publica Comercial
&nbsp;


|     Campo                     |     Tipo            |     Ejemplo                                                                                                                                                                           |     Descripción                                                                                                             |     URL                                                                                                      |
|-------------------------------|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     ikey                      |     varchar(50)     |     1                                                                                                                                                                                 |     Identificador de la Tabla (PK)                                                                                          |                                                                                                              |
|     id                        |     varchar(50)     |     Q2876002C                                                                                                                                                                         |     Identificador de l organización.                                                                                        |     https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/identifier    |
|     title                     |     varchar(400)    |     Instituto de Crédito Oficial (ICO)                                                                                                                                                |     Nombre o título de la entidad participante en la deuda   financiera.                                                    |                                                                                                              |
|     URL                       |     varchar(400)    |     https://datos.madrid.es/FwFront/portal_egob/new/img/portal_logo_h.png                                                                                                             |     URL de la organización.                                                                                                 |                                                                                                              |
|     contactPoint_email        |     varchar(200)    |     info@aytoxxx.com                                                                                                                                                                  |     Dirección de correo electrónico de la organización.                                                                     |                                                                                                              |
|     contactPoint_faxNumber    |     varchar(200)    |     1123333333                                                                                                                                                                        |     Número de fax de la organización.                                                                                       |                                                                                                              |
|     contactPoint_telephone    |     varchar(200)    |     1123333335                                                                                                                                                                        |     Número de teléfono de la organización.                                                                                  |                                                                                                              |
|     contactPoint_title        |     varchar(400)    |     Centro Cultural Ayto XXX                                                                                                                                                          |     Nombre del contacto de la organización.                                                                                 |                                                                                                              |
|     municipio_id              |     varchar(50)     |     28006                                                                                                                                                                             |     Identificador del municipio.                                                                                            |                                                                                                              |
|     municipio_title           |     varchar(200)    |     Alcobendas                                                                                                                                                                        |     Nombre del municipio.                                                                                                   |                                                                                                              |
|     distrito_id               |     varchar(50)     |     2800601                                                                                                                                                                           |     Identificador del distrito.                                                                                             |                                                                                                              |
|     distrito_title            |     varchar(200)    |     Distrito 1                                                                                                                                                                        |     Nombre del distrito.                                                                                                    |                                                                                                              |
|     street_address            |     varchar(200)    |     CALLE BUSTAMANTE V 16                                                                                                                                                             |     Dirección completa.                                                                                                     |                                                                                                              |
|     postal_code               |     varchar(10)     |     28045                                                                                                                                                                             |     Código postal.                                                                                                          |                                                                                                              |
|     portal_id                 |     varchar(50)     |     PORTAL000112                                                                                                                                                                      |     Id del portal.                                                                                                          |                                                                                                              |
|     classification            |     varchar(200)    |     administracion-general-estado      URI: http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica-financiera/tipo-entidad-prestamista/administracion-general-estado     |     SKOS:   http://vocab.linkeddata.es/page/datosabiertos/kos/economia/deuda-publica-financiera/tipo-entidad-prestamista    |                                                                                                              |


&nbsp;


&nbsp;
## TAXONOMÍAS SKOS <a name="id14"></a>
&nbsp;

### TIPO-ENTIDAD-PRESTAMISTA <a name="id15"></a>
&nbsp;
http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica-financiera/tipo-entidad-prestamista
Tesauro que recoge los tipos de entidades que pueden conceder préstamos a los ayuntamientos.
&nbsp;

|     Término                               |     Label                                         |
|-------------------------------------------|---------------------------------------------------|
|     administracion-general-estado         |     Administración General   del Estado           |
|     comunidad-autonoma                    |     Comunidad Autónoma                            |
|     consorcio-saneamiento-financiacion    |     Consorcio de saneamiento   de financiación    |
|     diputacion                            |     Diputación                                    |
|     entidad-financiera                    |     Entidad Financiera                            |
|     suscripcion-publica                   |     Suscripción Pública                           |
|     sector-privado-no-financiacion        |     Sector privado no de   financiación.          |
|     otra                                  |     Otra                                          |




&nbsp;
### TIPO-PRESTAMO <a name="id16"></a>
&nbsp;
http://vocab.linkeddata.es/datosabiertos/kos/economia/deuda-publica-financiera/tipo-prestamo
Tesauro que recoge los tipos de préstamo que puede tener un ayuntamiento como instrumento de financiación. Existen tres tipos principales que a su vez se dividen en subtipos.
&nbsp;


|     Tipo                             |     Subtipo                                                           |     Label                                                                                          |     Definición                                                                                                                                                                                                                                                                                |
|--------------------------------------|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     prestamo-fondo                   |                                                                       |     Préstamo Fondo                                                                                 |     Préstamos con cargo a   algún Fondo                                                                                                                                                                                                                                                       |
|                                      |     prestamo-fondo-impulso-economico                                  |     Préstamo Fondo de Impulso Económico                                                            |     Préstamos con cargo a este compartimento. RD-Ley   17/2014 (artículos 50-53).                                                                                                                                                                                                             |
|                                      |     prestamo-fondo-ordenacion                                         |     Préstamo Fondo de   Ordenación                                                                 |     Préstamos con cargo a   este compartimento. RD-Ley 17/2014 (artículo 39.1).                                                                                                                                                                                                               |
|                                      |     prestamo-fondo-liquidacion-financiación-pagos-proveedores-eell    |     Préstamo Fondo en Liquidación para la   financiación de los pagos a los proveedores de EELL    |     Préstamos con cargo a este compartimento. RD-Ley   17/2014 (artículo 39.2).                                                                                                                                                                                                               |
|     prestamo-entidad-prestamista     |                                                                       |     Préstamo entidad   prestamista                                                                 |     Préstamo concedido una o   más entidades prestamistas                                                                                                                                                                                                                                     |
|                                      |     bilateral                                                         |     Bilateral                                                                                      |     Préstamo concedido por una entidad prestamista                                                                                                                                                                                                                                            |
|                                      |     sindicado                                                         |     Sindicado                                                                                      |     Préstamo concedido por   una pluralidad de entidades prestamistas. Se caracteriza por el hecho de que   un grupo de Bancos o Cajas se reparten la financiación en determinada   proporción, es decir  conceden dinero   al prestatario en un determinado porcentaje cada uno de ellos.    |
|     anticipo-y-ayuda-reintegrable    |                                                                       |     Anticipo y ayuda reintegrable                                                                  |     Adelanto de una cantidad dineraria sin coste   financiero por parte del que la recibe y con la condición de devolver dichos   fondos pasado un tiempo determinado.                                                                                                                        |



&nbsp;








<p float="right" align="center">
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/gobEspana-logo.svg" alt="Logo Gobierno España" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/red-logo.svg" alt="Logo red.es" width="150"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ciudadesInteligentes-logo.svg" alt="Logo CiudadesInteligentes" width="150"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/unionEuropea-logo.svg" alt="Logo UnionEuropea" width="200"/>
</p>


<p float="right" align="center">
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntAcoruna-logo.svg" alt="Logo AyuntACoruña" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntMadrid-logo.svg" alt="Logo Madrid" width="100"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntSantiagoCompostela-logo.svg" alt="Logo Concello Santiago" width="200"/>
<img src="https://ciudadesabiertas.es/assets/img/cabiertas/ayuntZaragoza-logo.svg" alt="Logo Ayun.Zaragoza" width="200"/>
</p>




