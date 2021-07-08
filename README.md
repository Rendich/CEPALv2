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

# Configuración
Esta visualización  se crea con la funcion sunBurstSection, a través de los siguientes parámetros:
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
# Base y Agradecimientos
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
