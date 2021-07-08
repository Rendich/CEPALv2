# Visualización de Datos

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
        fileJson = 'data/my_input1.json';
        fileJson = 'data/my_input1_clean.json';
        idTable = '#idTable';
        stringTitle = "Metas ODS ";
        colLeft = 0;
        colRight = 3;
```
## Valores para la segunda visualización:
```
        colObjetive = "Meta ODS";
        colGroup = "PND_grupo";
        colSubgroup = "PND_subgrupo";
        arcClass = "pnd_class";
        stringObjetivoEstrategico = "Objetivo Estratégico";
        fileJson = 'data/my_input2.json';
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
