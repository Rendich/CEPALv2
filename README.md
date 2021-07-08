
# Visualización de Vínculos PND-ODS
Se desea visualizar los vínculos entre el Plan Nacional de Desarrollo de Paraguay y los Objetivos de Desarrollo Sostenible de la Agenda 2030. Se busca una visualización dinámica que sirva como mecanismo de difusión de los objetivos de desarrollo en el país para múltiples interesados, presentando el vínculo entre cada elemento del plan y su(s) correspondiente(s) objetivo(s).  
- Versión inicial disponible en: https://rendich-cepal.web.app.  
- Versión actual disponible en: https://rendich-cepal-v2.web.app.  

## Resumen
El Plan Nacional de Desarrollo (PND) consta de 16 objetivos estratégicos y 72  objetivos específicos. Por otro lado, los Objetivos de Desarrollo Sostenible (ODS) de la Agenda 2030 constan de 17 objetivos con 169 metas.
La visualización busca graficar dichas relaciones y estará diseñada para ser accedida desde equipos de pantalla grande (principalmente, notebook y computador de escritorio).

## Secciones y preguntas: 
Se definen las siguientes 3 secciones, donde cada una de ellas busca responder las siguientes preguntas:  
ODS:  Cómo se componen? Cómo se relaciona con PND?  
PND:  Cómo se compone? Cómo se relaciona con ODS?  
Relaciones: Cómo se interconectan PND y ODS? Cómo es la vinculación?  

## Exploración
### Sección Objetivos de Desarrollo Sostenible (ODS)
El gráfico de la izquierda muestra los Objetivos de Desarrollo Sostenible (ODS).  
El anillo más interno tiene 17 secciones, correspondientes a las 17 Metas ODS.  
![cepal1](https://user-images.githubusercontent.com/44811829/124857087-aa87de80-df79-11eb-9859-232fe0ac3bc7.gif)

Cada sección, u ODS, a su vez se compone de las secciones conectadas en el anillo externo, o Metas ODS, y su grosor de cada sección indica cuántos objetivos del PND están asociados. 

![cepal3](https://user-images.githubusercontent.com/44811829/124858635-7235cf80-df7c-11eb-8a18-87bfe4053217.gif)

Puedes navegar por el gráfico, o utilizando la lista de la izquierda, con lo que se actualiza la tabla de la derecha.
![cepal2](https://user-images.githubusercontent.com/44811829/124857893-1880d580-df7b-11eb-93ff-c07c8c23ae66.gif)

A modo de ejempo, las primera Metas del ODS 1:  
<img width="652" src="https://user-images.githubusercontent.com/44811829/124859535-1f5d1780-df7e-11eb-9598-d5dd91096ebf.png">

### Sección Plan Nacional de Desarrollo de Paraguay (PND). 
Esta sección es equivalente a la anterior, pero para el PND.  

### Sección Objetivos de Desarrollo Sostenible (ODS). 
Este gráfico muestra tanto ODS como PND, y al pasar el mouse muestra sus interconexiones:
![cepal4](https://user-images.githubusercontent.com/44811829/124860682-0eada100-df80-11eb-9385-de163cd7602b.gif)

La tabla asociada muestra la vinculación de las Metas ODS con los Objetivos PND.  
En este caso, las primeras filas del PND 4.4.2, donde se ven vinculaciones de los 3 tipos: Parcial, Contribución y Total:  
<img width="653" src="https://user-images.githubusercontent.com/44811829/124860862-7bc13680-df80-11eb-9825-6e449bef0621.png">

Además, los arcos internos muestran la cantidad de componentes de ODS u Objetivo Estratégico
![cepal5](https://user-images.githubusercontent.com/44811829/124878452-2003a700-df9a-11eb-8e09-d1c622ed51b4.gif)


# Aspectos Técnicos
## Configuración
Para la primera y segunda visualización se utiliza la funcion sunBurstSection:
```
sunBurstSection(fileCsv,
          divSelect,
          idSelect,
          colMetaODS,
          colGroup,
          colSubgroup,
          colObjetivoEstrategico,
          arcClass,
          stringObjetivoEstrategico,
          tableHeaders,
          idSVG,
          fileJson,
          idTable,
          stringTitle,
          colLeft,
          colRight,
          sunburstColor)
```
Para la tercera visualización se utiliza la función HierarchicalEdgeBundleSection:
```
          HierarchicalEdgeBundleSection(fileCsv,
            divSelect,
            idSelect,
            colODSsubgrupo,
            colPNDsubgrupo,
            colODSgrupo,
            colPNDgrupo,
            colMetaODS,
            colObjetivoPND,
            tableHeaders,
            idSVG,
            fileJson,
            idTable,
            colorHash)
```
            
## Valores para la primera visualización:
```
        fileCsv = "data/my_input1.csv";
        divSelect = "#divSelect";
        idSelect = "idSelect";
        colMetaODS = "Meta ODS";
        colObjetive = "Meta ODS";

        colGroup = "ODS_grupo";
        colSubgroup = "ODS_subgrupo";
        arcClass = "ods_class";

        colObjetivoEstrategico = 3;
        stringObjetivoEstrategico = "Objetivo Estratégico";
        tableHeaders = ["ODS","Meta ODS","Objetivo PND", "PND_grupo"];
        idSVG = '#partitionSVG1';
        fileJson = 'data/my_input1_clean.json';
        idTable = '#idTable';
        stringTitle = "Metas ODS ";
        colLeft = 0;
        colRight = 3;

        var sunburstColor = d3version4.scaleOrdinal().domain(d3version4.range(18))
          .range([
          "FFFFFF",
          "DC022F", "D4972D", "3F9336", "B80B24", "E72823",  "26B2E0", "F9B912", "900B35", "EC5324", "D30055",
          "F48B21", "B07B22", "336E36", "1D83CA", "4BB037",  "13558D", "123858", 
        ]);
        
```
## Valores para la segunda visualización:
```
        colObjetive = "Meta ODS";
        colGroup = "PND_grupo";
        colSubgroup = "PND_subgrupo";
        arcClass = "pnd_class";
        stringObjetivoEstrategico = "Objetivo Estratégico";
        fileJson = 'data/my_input2_clean.json';
        stringTitle = "Objetivos PND ";
        tableHeaders = ["PND_grupo","Objetivo PND","Meta ODS", "ODS"]
        fileCsv = "data/my_input2.csv";
        colObjetivoEstrategico = 0;
        colLeft = 3;
        colRight = 0;
        divSelect = "#divSelect2";
        idSelect = "idSelect2";

        colMetaODS = "Objetivo PND";
        idSVG = '#partitionSVG2';
        idTable = '#idTable2';
        sunburstColor = d3version4.scaleOrdinal().domain(d3version4.range(17))
                .range(["FFFFFF",
                "F2B729","F1B629", "F2B628", "F2B729",
                "F1B728", "1A3F7A", "1A3F79", "50872F",
                "F2B729", "1A3F79", "1A3F79", "508730",
                "F1B628", "E65631", "E55530", "508730"
              ]);
```


## Valores para la tercera visualización:
```
          fileCsv = "data/my_input3.csv"
          divSelect = "#divSelect3"
          idSelect = "idSelect3"
          colODSsubgrupo = "ODS_subgrupo"
          colPNDsubgrupo = "PND_subgrupo"
          colODSgrupo = "ODS_grupo"
          colPNDgrupo = "PND_grupo"
          colMetaODS = "Meta ODS"
          colObjetivoPND = "Objetivo PND"
          tableHeaders = ["Meta ODS", "Objetivo PND", "Vinculación"]
          idSVG = "#bundle"
          fileJson = "data/my_input3.json"
          idTable = '#idTable3'
          colorHash = {
            "ODS_1":"DC022F", "ODS_2":"D4972D", "ODS_3":"3F9336", "ODS_4":"B80B24", "ODS_5":"E72823", 
            "ODS_6":"26B2E0", "ODS_7":"F9B912", "ODS_8":"900B35", "ODS_9":"EC5324", "ODS_10":"D30055", 
            "ODS_11":"F48B21", "ODS_12":"B07B22", "ODS_13":"336E36", "ODS_14":"1D83CA", "ODS_15":"4BB037", 
            "ODS_16":"13558D", "ODS_17":"123858",

            "PND_1_1":"F2B729", "PND_1_2":"F1B629", "PND_1_3":"F2B628", "PND_1_4":"F2B729", 
            "PND_2_1":"F1B728", "PND_2_2":"1A3F7A", "PND_2_3":"1A3F79", "PND_2_4":"50872F",
            "PND_3_1":"F2B729", "PND_3_2":"1A3F79", "PND_3_3":"1A3F79", "PND_3_4":"508730",
            "PND_4_1":"F1B628", "PND_4_2":"E65631", "PND_4_3":"E55530", "PND_4_4":"508730",
          }
```


## Base
La primera y segunda visualización se basa en:
https://observablehq.com/@d3/zoomable-sunburst, con licencia ISC License.  
La tercera visualización se basa en:
https://observablehq.com/@d3/hierarchical-edge-bundling, con licencia ISC License.

```
Copyright 2018–2020 Observable, Inc.

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```
