## Consulta 1
### Consulta
¿Cuál es la evolución de deuda pública financiera del ayuntamiento?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=%23PC1+%C2%BFCu%C3%A1l+es+la+evoluci%C3%B3n+de+deuda+p%C3%BAblica+financiera+del+ayuntamiento%3F%0D%0APREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT++%3FfechaDeuda+%3FendeudamientoPDE+++%0D%0AWHERE+%7B+%3Fdeuda+a+esdeufin%3ADeudaAnual+.%0D%0A++++++++%3Fdeuda+dct%3Adate+%3FfechaDeuda+.%0D%0A++++++++%3Fdeuda+esdeufin%3AendeudamientoPDE+%3FendeudamientoPDE%0D%0A%7D%0D%0AORDER+BY+%3FfechaDeuda&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT  ?fechaDeuda ?endeudamientoPDE   
WHERE { ?deuda a esdeufin:DeudaAnual .
        ?deuda dct:date ?fechaDeuda .
        ?deuda esdeufin:endeudamientoPDE ?endeudamientoPDE
}
ORDER BY ?fechaDeuda
```  

## Consulta 2
### Consulta
¿Cual es el plan de amortizaciones de la deuda pública financiera del ayuntamiento?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT++%3Fanio+%28SUM%28%3Fimporte%29+AS+%3FimporteTotalAmortizacion%29++%0D%0AWHERE+%7B+%3Famort+a+esdeufin%3AAmortizacion+.%0D%0A++++++++%3Famort+dct%3Adate+%3FfechaAmortizacion+.%0D%0A++++++++BIND+%28YEAR%28%3FfechaAmortizacion%29+AS+%3Fanio%29+.%0D%0A++++++++%3Famort+esdeufin%3Aimporte+%3Fimporte%0D%0A%7D%0D%0AGROUP+BY+%3Fanio%0D%0AORDER+BY+%3Fanio&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT  ?anio (SUM(?importe) AS ?importeTotalAmortizacion)  
WHERE { ?amort a esdeufin:Amortizacion .
        ?amort dct:date ?fechaAmortizacion .
        BIND (YEAR(?fechaAmortizacion) AS ?anio) .
        ?amort esdeufin:importe ?importe
}
GROUP BY ?anio
ORDER BY ?anio
```  

## Consulta 3
### Consulta
¿Cuál es la deuda pública financiera por tipo de interés para el 30-06-2020?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%28sum%28%3Fimporte%29+as+%3Fdeuda%29+%3FtipoInteres+WHERE+%7B%0D%0A%09%3Fi+a+esdeufin%3AInstrumentoFinanciacion+.%0D%0A%09%3Fi++esdeufin%3AtipoInteres+%3FtipoInteres+.%0D%0A%09%3Fi++esdeufin%3AcapitalVivo+%3Fc+.%0D%0A++++++++OPTIONAL+%7B%3Fc++dct%3Adate+%3FfechaCapitalVivo+.%0D%0A%09++++++++++%3Fc++esdeufin%3Aimporte+%3Fimporte+.%0D%0A++++++++%7D%0D%0A%09FILTER+%28%3FfechaCapitalVivo+%3D+%222020-06-30%22%5E%5Exsd%3Adate%29%0D%0A%7D%0D%0AGROUP+BY+%3FtipoInteres&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT (sum(?importe) as ?deuda) ?tipoInteres WHERE {
	?i a esdeufin:InstrumentoFinanciacion .
	?i  esdeufin:tipoInteres ?tipoInteres .
	?i  esdeufin:capitalVivo ?c .
        OPTIONAL {?c  dct:date ?fechaCapitalVivo .
	          ?c  esdeufin:importe ?importe .
        }
	FILTER (?fechaCapitalVivo = "2020-06-30"^^xsd:date)
}
GROUP BY ?tipoInteres
```  

## Consulta 4
### Consulta
¿Cuál la deuda pública financiera por tipo de instrumento (emisión, préstamo) para el 30-06-2020?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=%23PC4++%C2%BFCu%C3%A1l+la+deuda+p%C3%BAblica+financiera+por+tipo+de+instrumento+%28emisi%C3%B3n%2C+pr%C3%A9stamo%29+para+el+30-06-2020%3F%0D%0APREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%28sum%28%3Fimporte%29+as+%3Fdeuda%29+%3FtipoInstrumento+where+%7B%0D%0A%09%3Fi++a+esdeufin%3AInstrumentoFinanciacion+.%0D%0A++++++++OPTIONAL+%7B%3Fi+esdeufin%3AcodISIN+%3FcodISIN+.%7D%0D%0A%09BIND+%28IF%28BOUND%28%3FcodISIN%29%2C%22Emision%22%2C%22Prestamo%22%29+AS+%3FtipoInstrumento%29%0D%0A%09%3Fi++esdeufin%3AcapitalVivo+%3Fc+.%0D%0A%09%3Fc++dct%3Adate+%3FfechaCapitalVivo+.%0D%0A%09%3Fc++esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09FILTER+%28%3FfechaCapitalVivo+%3D+%222020-06-30%22%5E%5Exsd%3Adate%29%0D%0A%7D%0D%0AGROUP+BY+%3FtipoInstrumento&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT (sum(?importe) as ?deuda) ?tipoInstrumento where {
	?i  a esdeufin:InstrumentoFinanciacion .
        OPTIONAL {?i esdeufin:codISIN ?codISIN .}
	BIND (IF(BOUND(?codISIN),"Emision","Prestamo") AS ?tipoInstrumento)
	?i  esdeufin:capitalVivo ?c .
	?c  dct:date ?fechaCapitalVivo .
	?c  esdeufin:importe ?importe .
	FILTER (?fechaCapitalVivo = "2020-06-30"^^xsd:date)
}
GROUP BY ?tipoInstrumento
```

## Consulta 5
### Consulta
¿Cuál es el importe de la deuda préstamos en un determinado plazo, por ejemplo entre 1 y 5 años?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3EPREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%28sum%28%3Fimporte%29+as+%3FimportePrestamo%29++where+%7B%0D%0A%09%3Fi++a+esdeufin%3APrestamo+.%0D%0A%09%3Fi++esdeufin%3AcapitalVivo+%3Fc+.%0D%0A%09%3Fc++dct%3Adate+%3FfechaCapitalVivo+.%0D%0A%09%3Fc++esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09%3Fi+esdeufin%3AfechaVencimiento+%3FfechaVencimiento+.%0D%0A%09FILTER+%28%28%28YEAR%28%3FfechaVencimiento%29-2020%29+%3C%3D+5%29+%26%26+%28%28YEAR%28%3FfechaVencimiento%29-2020%29+%3E%3D+1%29+%26%26+%28YEAR%28%3FfechaCapitalVivo%29%3D%222020%22%5E%5Exsd%3Ainteger%29%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
#Se tomó el año 2020 como año actual 
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX dct:<http://purl.org/dc/terms/>PREFIX dct:<http://purl.org/dc/terms/>

SELECT (sum(?importe) as ?importePrestamo)  where {
	?i  a esdeufin:Prestamo .
	?i  esdeufin:capitalVivo ?c .
	?c  dct:date ?fechaCapitalVivo .
	?c  esdeufin:importe ?importe .
	?i esdeufin:fechaVencimiento ?fechaVencimiento .
	FILTER (((YEAR(?fechaVencimiento)-2020) <= 5) && ((YEAR(?fechaVencimiento)-2020) >= 1) && (YEAR(?fechaCapitalVivo)="2020"^^xsd:integer))
}
``` 
## Consulta 6
### Consulta
¿Cuál es el ranking de entidades prestamistas por número de préstamos concedidos al ayuntamiento?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+org%3A%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Forg%23%3E%0D%0APREFIX+foaf%3A%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fnombre+%28count%28%3Fprestamo%29+as+%3FnumPrestamos%29++where+%7B%0D%0A%09%3Fprestamo++a+esdeufin%3APrestamo+.%0D%0A%09%3Fprestamo+esdeufin%3AentidadPrestamista+%3Fentidad+.%0D%0A%09%3Fentidad+foaf%3Aname+%3Fnombre%0D%0A%7D%0D%0AGROUP+BY+%3Fnombre%0D%0AORDER+BY+DESC%28%3FnumPrestamos%29&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX org:<http://www.w3.org/ns/org#>
PREFIX foaf:<http://xmlns.com/foaf/0.1/>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT ?nombre (count(?prestamo) as ?numPrestamos)  where {
	?prestamo  a esdeufin:Prestamo .
	?prestamo esdeufin:entidadPrestamista ?entidad .
	?entidad foaf:name ?nombre
}
GROUP BY ?nombre
ORDER BY DESC(?numPrestamos)
}
```
## Consulta 7
### Consulta
¿Cuales son  los detalles de los préstamos de un ayuntamiento a partir de cierto año?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+org%3A%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Forg%23%3E%0D%0APREFIX+foaf%3A%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0Aselect+*+where+%7B%0D%0A%23SELECT+%3Fdescripcion+%3FentidadPrestamista+%3FtipoPrestamo+%3Fimporte+%3FtipoInteres+%3FfechaFormal+%3Fplazo+where+%7B%0D%0A%09%3Fprestamo++a+esdeufin%3APrestamo+.%0D%0A%09%3Fprestamo+dct%3Adescription+%3Fdescripcion+.%0D%0A%09%3Fprestamo+esdeufin%3AentidadPrestamista+%3Fentidad+.%0D%0A%09%3Fentidad+foaf%3Aname+%3FentidadPrestamista+.%0D%0A%09%3Fprestamo+esdeufin%3AtipoPrestamo+%3Ftipop+.%0D%0A%09%3Ftipop+skos%3AprefLabel+%3FtipoPrestamo+.%0D%0A%09%3Fprestamo+esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09%3Fprestamo+esdeufin%3AtipoInteres+%3FtipoInteres+.%0D%0A%09%3Fprestamo+esdeufin%3AfechaFormalizacion+%3FfechaFormal+.%0D%0A%09FILTER+%28%3FfechaFormal+%3E+%222010-01-01%22%5E%5Exsd%3Adate%29%0D%0A%7D&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
#A partir del 2010
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX org:<http://www.w3.org/ns/org#>
PREFIX foaf:<http://xmlns.com/foaf/0.1/>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT ?descripcion ?entidadPrestamista ?tipoPrestamo ?importe ?tipoInteres ?fechaFormal  where {
	?prestamo  a esdeufin:Prestamo .
	?prestamo dct:description ?descripcion .
	?prestamo esdeufin:entidadPrestamista ?entidad .
	?entidad foaf:name ?entidadPrestamista .
	?prestamo esdeufin:tipoPrestamo ?tipoPrestamo .
	?prestamo esdeufin:importe ?importe .
	?prestamo esdeufin:tipoInteres ?tipoInteres .
	?prestamo esdeufin:fechaFormalizacion ?fechaFormal .
	FILTER (?fechaFormal > "2010-01-01"^^xsd:date)
}
``` 
## Consulta 8
### Consulta
¿Cuales son todos los préstamos concedidos por determinada entidad prestamista?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+org%3A%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Forg%23%3E%0D%0APREFIX+foaf%3A%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fdescripcion+%3Fimporte+%3FtipoInteres+%3FfechaFormal+where+%7B%0D%0A%09%3Fprestamo++a+esdeufin%3APrestamo+.%0D%0A%09%3Fprestamo+dct%3Adescription+%3Fdescripcion+.%0D%0A%09%3Fprestamo+esdeufin%3AentidadPrestamista+%3Fentidad+.%0D%0A%09%3Fentidad+org%3Aidentifier+%220182%22%5E%5Exsd%3Astring+.%0D%0A%09%3Fprestamo+esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09%3Fprestamo+esdeufin%3AtipoInteres+%3FtipoInteres+.%0D%0A%09%3Fprestamo+esdeufin%3AfechaFormalizacion+%3FfechaFormal+.%0D%0A%7D&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
#0182 BBVA
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX org:<http://www.w3.org/ns/org#>
PREFIX foaf:<http://xmlns.com/foaf/0.1/>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT ?descripcion ?importe ?tipoInteres ?fechaFormal where {
	?prestamo  a esdeufin:Prestamo .
	?prestamo dct:description ?descripcion .
	?prestamo esdeufin:entidadPrestamista ?entidad .
	?entidad org:identifier "0182"^^xsd:string .
	?prestamo esdeufin:importe ?importe .
	?prestamo esdeufin:tipoInteres ?tipoInteres .
	?prestamo esdeufin:fechaFormalizacion ?fechaFormal .
}
``` 
## Consulta 9
### Consulta
¿Cuales son todos los detalles de las emisiones de un ayuntamiento a partir de cierto año?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+org%3A%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Forg%23%3E%0D%0APREFIX+foaf%3A%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fdescripcion+%3Fimporte+%3FtipoInteres+%3FnumeroTitulos+%3FcuantiaPorTitulo+%3FfechaEmision+%3Fduracion++where+%7B%0D%0A%09%3Femision++a+esdeufin%3AEmision+.%0D%0A%09%3Femision+dct%3Adescription+%3Fdescripcion+.%0D%0A%09%3Femision+esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09%3Femision+esdeufin%3AtipoInteres+%3FtipoInteres+.%0D%0A%09%3Femision+esdeufin%3AnumeroTitulos+%3FnumeroTitulos+.%0D%0A%09%3Femision+esdeufin%3AcuantiaPorTitulo+%3FcuantiaPorTitulo+.%0D%0A%09%3Femision+esdeufin%3AfechaEmision+%3FfechaEmision+.%0D%0A%09%3Femision+esdeufin%3Aduracion+%3Fduracion+.%0D%0A%09%23FILTER+%28%3FfechaEmision+%3E+%222005-01-01%22%5E%5Exsd%3Adate%29%0D%0A%7D&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX org:<http://www.w3.org/ns/org#>
PREFIX foaf:<http://xmlns.com/foaf/0.1/>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT ?descripcion ?importe ?tipoInteres ?numeroTitulos ?cuantiaPorTitulo ?fechaEmision ?duracion  where {
	?emision  a esdeufin:Emision .
	?emision dct:description ?descripcion .
	?emision esdeufin:importe ?importe .
	?emision esdeufin:tipoInteres ?tipoInteres .
	?emision esdeufin:numeroTitulos ?numeroTitulos .
	?emision esdeufin:cuantiaPorTitulo ?cuantiaPorTitulo .
	?emision esdeufin:fechaEmision ?fechaEmision .
	?emision esdeufin:duracion ?duracion .
	#FILTER (?fechaEmision > "2005-01-01"^^xsd:date)
}
```
## Consulta 10
### Consulta
¿Cuales son los detalles de una determinada emisión?
[Resultado](http://ciudadesabiertas.linkeddata.es/sparql?default-graph-uri=&query=PREFIX+esdeufin%3A%3Chttp%3A%2F%2Fvocab.ciudadesabiertas.es%2Fdef%2Feconomia%2Fdeuda-publica-financiera%23%3E%0D%0APREFIX+skos%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0APREFIX+xsd%3A%3Chttp%3A%2F%2Fwww.w3.org%2F2001%2FXMLSchema%23%3E%0D%0APREFIX+org%3A%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Forg%23%3E%0D%0APREFIX+foaf%3A%3Chttp%3A%2F%2Fxmlns.com%2Ffoaf%2F0.1%2F%3E%0D%0APREFIX+dct%3A%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0D%0A%0D%0ASELECT+%3Fdescripcion+%3Fimporte+%3FtipoInteres+%3FnumeroTitulos+%3FcuantiaPorTitulo+%3FfechaEmision+%3Fduracion++where+%7B%0D%0A%09%3Femision++a+esdeufin%3AEmision+.%0D%0A%09%3Femision+esdeufin%3AcodISIN+%22ES0201001130%22%5E%5Exsd%3Astring+.%0D%0A%09%3Femision+dct%3Adescription+%3Fdescripcion+.%0D%0A%09%3Femision+esdeufin%3Aimporte+%3Fimporte+.%0D%0A%09%3Femision+esdeufin%3AtipoInteres+%3FtipoInteres+.%0D%0A%09%3Femision+esdeufin%3AnumeroTitulos+%3FnumeroTitulos+.%0D%0A%09%3Femision+esdeufin%3AcuantiaPorTitulo+%3FcuantiaPorTitulo+.%0D%0A%09%3Femision+esdeufin%3AfechaEmision+%3FfechaEmision+.%0D%0A%09%3Femision+esdeufin%3Aduracion+%3Fduracion+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+
)

### Consulta SPARQL
```
P#Código ES0201001130
PREFIX esdeufin:<http://vocab.ciudadesabiertas.es/def/economia/deuda-publica-financiera#>
PREFIX skos:<http://www.w3.org/2004/02/skos/core#>
PREFIX xsd:<http://www.w3.org/2001/XMLSchema#>
PREFIX org:<http://www.w3.org/ns/org#>
PREFIX foaf:<http://xmlns.com/foaf/0.1/>
PREFIX dct:<http://purl.org/dc/terms/>

SELECT ?descripcion ?importe ?tipoInteres ?numeroTitulos ?cuantiaPorTitulo ?fechaEmision ?duracion  where {
	?emision  a esdeufin:Emision .
	?emision esdeufin:codISIN "ES0201001130"^^xsd:string .
	?emision dct:description ?descripcion .
	?emision esdeufin:importe ?importe .
	?emision esdeufin:tipoInteres ?tipoInteres .
	?emision esdeufin:numeroTitulos ?numeroTitulos .
	?emision esdeufin:cuantiaPorTitulo ?cuantiaPorTitulo .
	?emision esdeufin:fechaEmision ?fechaEmision .
	?emision esdeufin:duracion ?duracion .
}
```  





