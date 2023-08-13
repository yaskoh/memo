# Spring Framework
## About
- Javaプラットフォーム向けのオープンソース・アプリケーションフレームワーク。
  特定のプログラミングモデルを強制するものではないが、EJBモデルの代替・置換・追加として広く認知されつつある。
## APIs
### 4.3.6
- [[http://docs.spring.io/spring/docs/current/javadoc-api/][Spring Framework 4.3.6 RELEASE API]]
#### Packages
##### org.springframework.beans.factory
###### Interfaces
####### BeanFactory
######## Fields
######## Methods
######### getBean(Class<T> requiredType)
- Return the bean instance that uniquely matches the given object type, if any.
####### ListableBeanFactory
######## Fields
######## Methods
##### org.springframework.context
###### Interfaces
####### ConfigurableApplicationContext
####### ApplicationContext
- public interface ApplicationContext extends EnvironmentalCapable, ListableBeanFactory, HierarchicalBeanFactory, MessageSource, ApplicationEventPublisher, ResourcePatternResolver
- Central interface to provide configuration for an application.
######## Fields
######## Methods
##### org.springframework.stereotype
###### Annotations
####### Component
- Indicates that an annotated class is a "Component".
####### Controller
- Indicates that an annotated class is a "Controller"
####### Repository
- Indicates that an annotated class is a "Repository"
####### Service
- Indicates that an annotated class is a "Service"
## Documents
### 5.1.9
- https://docs.spring.io/spring/docs/current/spring-framework-reference/index.html
#### Overview
#### Core
##### 1. The IoC Container
##### 2. Resources
##### 3. Validation, Data Binding, and Type Conversion
##### 4. Spring Expression Language (SpEL)
##### 5. Aspect Oriented Programming with Spring
##### 6. Spring AOP APIs
##### 7. Null-safety
##### 8. Data Buffers andCodecs
##### 9. Appendix
#### Testing
#### Data Access
#### Web Servlet
##### 1. Spring Web MVC
###### 1.9 View Technologies
####### 1.9.5 JSP and JSTL
######## View Resolvers
######## JSPs versus JSTL
######## Spring's JSP Tag Library
######## Spring's form tag library
######### Configuration
######### The Form Tag
- <from:form>
######### The input Tag
######### The checkbox Tag
######### The checkboxes Tag
######### The radiobutton Tag
######### The radiobuttons Tag
######### The password Tag
######### The select Tag
######### The option Tag
######### The options Tag
######### The textarea Tag
######### The hidden Tag
######### The errors Tag
######### HTTP Method Conversion
######### HTML5 Tags
##### 2. REST Clients
##### 3. Testing
##### 4. WebSockets
##### 5. Other Web Frameworks
#### Web Reactive
#### Integration
#### Languages
## Tools
### Spring Tool Suite (STS)
#### application.propertiens
 - 
#### Memo
##### KeybindをEmacsに変更
- Spring Tool Suite 3 -> 環境設定 -> General -> Keys
  Schemeをdefault -> Emacsに変更
## Link
- [[http://projects.spring.io/spring-framework/][spring]]
- [[http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/][Spring Framework Documnetation]]
- [[https://docs.spring.io/spring/docs/4.3.12.RELEASE/spring-framework-reference/htmlsingle/][Spring Framework Reference Documentaiton - 4.3.12.RELEASE]]
- [[http://docs.spring.io/spring/docs/current/javadoc-api/][Spring Framework RELEASE API]]

- [[https://spring.io/guides][spring GUIDES]]

- [[http://dev.classmethod.jp/series/spring-framework/][連載 Spring framework – シリーズ – - Developers.IO]]

