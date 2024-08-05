# CSV to DMN converter
## How can it benefit you?
The purpose of this program is to convert a CSV file to a DMN table and vice versa. This enables you to use e.g. Excel functions to enter information into the DMN table.

## How does it work?
The program is reading the CSV, which has to be in a particular layout, into an object, this is then creating a `DmnModelInstance` (class provided by Camunda), this instance is then exported to a DMN file.
On your .jar file (located in the target folder), which you got from compiling the project with maven, run following command:

* `mvn clean install compile`
* `cd target/`
  * Move your cursor to target folder, where the .jar are generated
* `java -jar csv2dmn-converter-jar-with-dependencies.jar [-c] [-d] -i inputFile -o outputFile`
  * Selected the "with-dependencies" one
  * Either -c or -d must be provided!!
  * `-c,--csv-to-dmn                   Convert CSV to DMN`
  * `-cv,--include-camunda-variables   Include Camunda variables`
  * `-d,--dmn-to-csv                   Convert DMN to CSV`
  * `-i,--input-file <arg>             Input file (CSV or DMN)`
  * `-o,--output-file <arg>            Output file (CSV or DMN)`


## Example
Your CSV-File (values separated with comma!!) should look like this (further explanation below)
![Origin CSV][origin-csv]

Then on your .jar file in your target folder, which you got from compiling it with Maven run this command:
![Command][command]

Your outcome should be following:
![Outcome DMN][outcome-dmn]





## Layout of a compatible file

The CSV needs following format in order to be able to be picked up by the program. All the fields are described afterwards.
Imagine the table below is a CSV opened in Excel.

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