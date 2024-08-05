# CSV to DMN converter
## Allows
* ".csv" < - (both senses) - > ".dmn"
  * -> Excel functions -- can be used to -- enter information | DMN table

## How does it work?
* read the CSV / must be | particular layout (an object)
* `DmnModelInstance` (class provided by Camunda) is created / 
  * it's exported -- to a -- ".dmn"
* | your ".jar"'s location -> run next commands

## How to run it?
* `mvn clean install compile`
* `cd target/`
  * Move your cursor to target folder, where the .jar are generated
* `java -jar csv2dmn-converter-jar-with-dependencies.jar [-c] [-d] -i inputFile -o outputFile`
  * Selected the "with-dependencies" one
  * 👁️Either `-c` OR `-d` must be provided!! 👁️
  * `-c,--csv-to-dmn`
    * == CSV -> DMN
  * `-cv,--include-camunda-variables`
    * == Include Camunda variables
  * `-d,--dmn-to-csv`
    * == DMN -> CSV
  * `-i,--input-file <arg>`
    * == Input file (CSV or DMN)
  * `-o,--output-file <arg>`
    * == Output file (CSV or DMN)


## Example
* Given a .csv / 👁️ values separated with comma 👁️
![Origin CSV](./docs/OriginCSV.png)

* compile the Maven project
* | your .jar file location (under /target), run 
![Command](./docs/Command.png)
* your outcome should be
![Outcome DMN](./docs/OutcomeDMN.png)


## CSV formatting rules
* requirements
  * row1
    * description of each column
  * always needed >=1 input & >=1 output
* _Example:_

. | A | B | C | D | E | F | G
--- | --- | --- | --- | --- |--- |--- |---
1 | DmnId | Title | Hit Policy |  |  |  |  
2 | Input | Input | Input | Output | Output | |   
3 | ColumnName1 | ColumnName1 | ColumnName1 | ColumnName1 | ColumnName1 |  | 
4 | string | integer | boolean | date | double |  |  
5 | SomeString | 301 | true | date(“2020-12-31”) | 12.01 | CommentsHere |  
6 | OtherString | 1337 | false | date(“2021-01-01”) | 123.45 | CommentsHere |

## Notes:
* Forked repo from [CsvToDmnConverter](https://github.com/camunda-community-hub/CsvToDmnConverter)
* You could check more detailed information in that repo 