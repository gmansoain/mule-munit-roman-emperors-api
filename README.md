<h1>Mule MUnit Roman Emperors API</h1>


## Description

## Set up MUnit DB Server for mocking the real DB server
1. Create a new Test Suite for the getEmperors flow --> right-click on the flow and select _MUnit/Create Blank Test for this flow_
2. Rename the Test Suite to _getEmperors-test-suite.xml_
3. Rename the Test case to _getEmperorsSuccessTestCase_

### MUnit DB Server Setup
4. From the MUnit Test suite add the MUnit DB server from the _Mule Palette_. Search on Exchange
5. Verify the MUnit DB server has been added as a dependency in the pom file
```xml
<dependency>
	<groupId>com.mulesoft.munit.utils</groupId>
	<artifactId>munit-dbserver-module</artifactId>
	<version>2.0.2</version>
	<classifier>mule-plugin</classifier>
</dependency>
```
7. Create a file _emperors.csv_ with the content of your DB under _src/test/resources_. For this project:
```csv
"id","name","reign_start","reign_end","birth_date","death_date","dynasty","other_titles","biography"
1,"Augustus","27 BC","14 AD","63 BC","14 AD","Julio-Claudian","Imperator Caesar Divi Filius Augustus","Augustus was the first Roman emperor, ruling from 27 BC until his death in 14 AD. He was the founder of the Roman Principate and the first ruler of the Julio-Claudian dynasty."
2,"Tiberius","14 AD","37 AD","42 BC","37 AD","Julio-Claudian","Imperator Tiberius Caesar Divi Augusti Filius Augustus","Tiberius was the second Roman emperor, succeeding Augustus. He ruled from 14 AD until his death in 37 AD."
3,"Caligula","37 AD","41 AD","12 AD","41 AD","Julio-Claudian","Gaius Caesar Augustus Germanicus","Caligula was the third Roman emperor, ruling from 37 AD until his assassination in 41 AD."
4,"Claudius","41 AD","54 AD","10 BC","54 AD","Julio-Claudian","Tiberius Claudius Caesar Augustus Germanicus","Claudius was the fourth Roman emperor, ruling from 41 AD until his death in 54 AD. He was known for his expansion of the empire and public works."
5,"Nero","54 AD","68 AD","37 AD","68 AD","Julio-Claudian","Nero Claudius Caesar Augustus Germanicus","Nero was the fifth Roman emperor, ruling from 54 AD until his death in 68 AD. His reign was marked by extravagance and persecution of Christians."
6,"Galba","68 AD","69 AD","3 BC","69 AD","Year of the Four Emperors","Servius Sulpicius Galba Caesar Augustus","Galba was the sixth Roman emperor, ruling for a brief period from 68 AD until his assassination in 69 AD."
7,"Otho","69 AD","69 AD","32 AD","69 AD","Year of the Four Emperors","Marcus Salvius Otho Caesar Augustus","Otho was the seventh Roman emperor, ruling for a few months in 69 AD until his suicide."
8,"Vitellius","69 AD","69 AD","15 AD","69 AD","Year of the Four Emperors","Aulus Vitellius Germanicus Augustus","Vitellius was the eighth Roman emperor, ruling for a few months in 69 AD until his execution."
9,"Vespasian","69 AD","79 AD","9 AD","79 AD","Flavian","Titus Flavius Caesar Vespasianus Augustus","Vespasian was the ninth Roman emperor, ruling from 69 AD until his death in 79 AD. He founded the Flavian dynasty."
10,"Titus","79 AD","81 AD","39 AD","81 AD","Flavian","Titus Flavius Caesar Vespasianus Augustus","Titus was the tenth Roman emperor, ruling from 79 AD until his death in 81 AD. He is remembered for his generosity and efforts during the eruption of Mount Vesuvius."
11,"Domitian","81 AD","96 AD","51 AD","96 AD","Flavian","Titus Flavius Caesar Domitianus Augustus","Domitian was the eleventh Roman emperor, ruling from 81 AD until his assassination in 96 AD."
12,"Nerva","96 AD","98 AD","30 AD","98 AD","Nerva-Antonine","Marcus Cocceius Nerva Caesar Augustus","Nerva was the twelfth Roman emperor, ruling from 96 AD until his death in 98 AD. He was known for his benevolence and efforts to restore the Senate."
13,"Trajan","98 AD","117 AD","53 AD","117 AD","Nerva-Antonine","Caesar Nerva Traianus Augustus","Trajan was the thirteenth Roman emperor, ruling from 98 AD until his death in 117 AD. He presided over one of the greatest expansions of the Roman Empire."
14,"Hadrian","117 AD","138 AD","76 AD","138 AD","Nerva-Antonine","Publius Aelius Hadrianus Augustus","Hadrian was the fourteenth Roman emperor, ruling from 117 AD until his death in 138 AD. He is known for his extensive travels and architectural projects."
15,"Antoninus Pius","138 AD","161 AD","86 AD","161 AD","Nerva-Antonine","Titus Aelius Hadrianus Antoninus Augustus Pius","Antoninus Pius was the fifteenth Roman emperor, ruling from 138 AD until his death in 161 AD. He was known for his peaceful reign and promotion of the arts."
16,"Romulus Augustulus","October 31, 475 AD","September 4, 476 AD","Unknown","Unknown","Non-dynastic","Augustus","The last Roman emperor, deposed by Odoacer."
17,"Romulus Augustulus","October 31, 475 AD","September 4, 476 AD","Unknown","Unknown","Non-dynastic","Augustus","The last Roman emperor, deposed by Odoacer."
18,"Romulus Augustulus","October 31, 475 AD","September 4, 476 AD","Unknown","Unknown","Non-dynastic","Augustus","The last Roman emperor, deposed by Odoacer."

```
7. In the _getEmperors-test-suite_ munit file use the _Global Elements_ tab and create a new Element _MUnit DB Server Config_ with the following values:
	- Csv: _emperors.csv_ (the csv file with the content of your DB)
	- Database: _ancient_rome_ (the name of the real database)
	- Connection string parameters: _MODE=MySQL_
7. In the _getEmperors-test-suite_ munit file use the _Global Elements_ tab and create a new Element _Database Config_ with the following values:
	- Name: 
	```
	Database_Config_MUNIT
	```
	- Connection: _Generic Connection_
	- URL: 
	```
	jdbc:h2:tcp://localhost/mem:ancient_rome
	```
	- Driver Class name: 
	```
	org.h2.Driver
	```
7. Create Properties file under src/main/resources/properties.yaml. This is pointing to the real DB server configuration
```yaml
db-config: "Database_Config_MYSQL"
```
8. In the _global.xml_ file create a new Element _Configuration Properites_ pointing to _properties.yaml_
9. In the _getEmperors-test-suite_ munit file use the _Global Elements_ tab and create a new Element _Configuration Properties_ pointing to _properties-munit.xml_
8. Create Properties file under src/test/resources/properties-munit.yaml. This is pointing to the Mock DB server configuration
```yaml
db-config: "Database_Config_MUNIT"
```

7. In the testSuite, click on the Global Elements tab and create:



## Links
- [How to create your first MUnit test in Anypoint Studio](https://developer.mulesoft.com/tutorials-and-howtos/quick-start/how-to-create-your-first-munit-test-in-anypoint-studio/)
