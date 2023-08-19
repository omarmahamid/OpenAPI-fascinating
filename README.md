# OpenAPI-fascinating
open api generator using maven is fascinating tools


# config the plugin

by adding this plugin build

````
<build>
        <plugins>

            <plugin>
                <groupId>org.openapitools</groupId>
                <artifactId>openapi-generator-maven-plugin</artifactId>
                <version>${openapi.maven.plugin}</version>


                <executions>

                    <execution>
                        <goals>
                            <goal>generate</goal>
                        </goals>
                        <configuration>
                            <inputSpec>${project.basedir}/src/main/resources/service-api.yaml</inputSpec>
                            <generatorName>spring</generatorName>
                            <library>spring-boot</library>
                            <generateApis>true</generateApis>
                            <generateApiTests>false</generateApiTests>
                            <generateApiDocumentation>false</generateApiDocumentation>
                            <generateModels>true</generateModels>
                            <generateModelTests>false</generateModelTests>
                            <generateModelDocumentation>false</generateModelDocumentation>
                            <generateSupportingFiles>true</generateSupportingFiles>
                            <configOptions>
                                <useSpringBoot3>true</useSpringBoot3>
                                <interfaceOnly>true</interfaceOnly>
                                <useBeanValidation>true</useBeanValidation>
                                <performBeanValidation>true</performBeanValidation>
                                <serializableModel>true</serializableModel>
                                <apiPackage>org.training.api</apiPackage>
                                <modelPackage>org.training.api.model</modelPackage>
                            </configOptions>
                        </configuration>
                    </execution>

                </executions>
            </plugin>


        </plugins>
    </build>

  ````

you can see generating spec yaml file.

for example: 

````
openapi: 3.0.0
info:
  title: Training DTO Definition
  version: 1.0.0

components:
  schemas:
    trainingDTO:
      type: object
      properties:
        id:
          type: integer
          format: int64
        name:
          type: string
        startDate:
          type: string
          format: date
        endDate:
          type: string
          format: date
        instructor:
          type: string
      required:
        - id
        - name
        - startDate
        - endDate

paths:
  /training/{id}:
    get:
      summary: Get training by ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: integer
            format: int64
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/trainingDTO'

````


once you adding both and spring dependency and swagger dependency.


run 
mvn clean install


and after that you will see the fascinate generated classes

1. TrainingDTO 
2. TrainingAPI working with spring !
