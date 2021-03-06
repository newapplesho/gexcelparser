GExcelParser
=========

Excelシートのデータを、[GroovyCSV](https://github.com/xlson/groovycsv)ライクに取り出すためのライブラリです。


## 利用例
### build.gradle

```groovy
// build.gradle (minimum)
apply plugin: 'groovy'

repositories {
    jcenter()

    // gexcelapi
    maven {
        url 'http://dl.bintray.com/nobeans/maven'
    }
    
    // gexcelparser
    maven { 
        url 'https://github.com/sorabito/gexcelparser/raw/master/repository' 
    }
}

dependencies {
    compile 'org.codehaus.groovy:groovy-all:2.4.7'
    compile 'com.sorabito:gexcelparser:1.0.2'
}
```

### Excelシート (sample.xml - Sheet1)

|column1|column2     |
| ----- | ---------- |
|1      | word       |
|2      | excel      |
|3      | power point|


### スクリプト

```groovy

import com.sorabito.gexcelparser.*

GExcelParser parser = GExcelParser.open('path/to/sample.xlsx')
List<PropertyMapper> mapperList = parser.parseSheet('Sheet1')

mapperList.each { mapper ->
    println "${mapper.column1}: ${mapper.column2}"
}
```


## License

[Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0)

