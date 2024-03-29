# Selenium
## Selenium WebDriver
### About
- 起動
  java -jar selenium-server-standalone-*.jar

### Architecture
- 
  各種ブラウザごとにドライバが用意されており、
  それらのドライバはJSON Wire ProtocolというSeleniumが定義しているRESTful APIに対応している。

- 
  ◆HTTP Client, Client Library (Java, Ruby, Python, C#, Perl, PHP, Javascript(Node.js))
    ↑ 
    JSON Wire Protocol
    ↓
  ◆Browser Drivers (Firefox Driver, Chrome Drive, IE Driver, etc.)
    ↑
    ブラウザの拡張機能、OSネイティブ機能
    ↓
  ◆Browser

#### Drivers
- 
  各ドライバによって形式や操作方法はさまざま。

##### Firefoxドライバ
- 
  Firefoxの拡張機能

##### Chromeドライバ
- 
  実行ファイル（バイナリ）
  http://chromedriver.storage.googleapis.com/index.html

#### Selenium Server
- 
  特定のドライバに対応していないライブラリの場合、Selenium Serverを利用する必要がある。
  Node.jsの2.44.0で対応しているのはFirefoxとChromeのみなので、その他のブラウザを利用したい場合など。
  
  Selenium ServerはJavaで書かれたサーバーで、クライアントとドライバの中継サーバとして振る舞うため、
  クライアントライブラリがドライバの管理をする必要がなくなる。
  
  公式ライブラリが用意されていない言語ではサードパーティクライアントが多数公開されているが、
  Selenium Serverの利用を前提としている場合が多い。

- 
  次のコマンドで起動する。
  java -jar selenium-server-standalone-xxx.jar

- Download
  http://www.seleniumhq.org/download/

- 
  ◆HTTP Client, Client Library (Java, Ruby, Python, C#, Javascript(Node.js))
    ↑ 
    JSON Wire Protocol
    ↓
  ◆Selenium Server
    ↑ 
    JSON Wire Protocol
    ↓
  ◆Browser Drivers (Firefox Driver, Chrome Drive, IE Driver, etc.)
    ↑
    ブラウザの拡張機能、OSネイティブ機能
    ↓
  ◆Browser

### Setting up
#### Python
- pip install selenium
#### Java
#### C#
#### Ruby
#### Perl
#### JS
### API
#### Python
- version 2.53.6
##### selenium
###### common
####### selenium.common.exceptions
######## exception TimeoutException
- TimeoutException(msg=None, screeen=None, stacktrace=None)
  Thrown when a command does not complete in enough time.
######## exception WebDriverException
- WebDriverException(msg=None, screen=None, stacktrace=None)
  Base webdriver exception.
###### webdriver
####### android
####### blackberry
####### chrome
######## selenium.webdriver.chrome.options
######## selenium.webdriver.chrome.remote_connection
######## selenium.webdriver.chrome.service
######## selenium.webdriver.chrome.webdriver
######### class
########## WebDriver(RemoteWebDriver)
- needin to download the ChromeDriver.
########### Methods
############ __init__(self, executable_path="chromedriver", port=0, chrome_options=None, service_args=None, desired_capabilities=None, service_log_path=None)
####### common
######## html5
######### selenium.webdriver.common.html5.application_cache
######## selenium.webdriver.common.action_chains
######## selenium.webdriver.common.alert
######## selenium.webdriver.common.by
######### class
########## By(object)
- Set of supported locator strategies.
  
- Elements
  - ID
  - XPATH
  - LINK_TEXT
  - PARTIAL_LINK_TEXT
  - NAME
  - TAG_NAME
  - CLASS_NAME
  - CSS_SELECTOR
######## selenium.webdriver.common.desired_capabilities
######## selenium.webdriver.common.keys
######## selenium.webdriver.common.proxy
######## selenium.webdriver.common.service
######### class
########## Service(object)
########### Methods
############ __init__(self, executable, port=0, log_file=PIPE, env=None, start_error_message="")
############ command_line_args(self)
############ start(self)
############ stop(self)
- Stops the service.
############ __del__(self)
########### Properties
############ service_url(self)
######## selenium.webdriver.common.touch_actions
######## selenium.webdriver.common.util
####### edge
######## selenium.webdriver.edge.webdriver
######### class
########## WebDriver
########### Methods
############ __init__(self, executable_path='MicrosoftWebDriver.exe', capabilities=None, port=0)
####### firefox
######## selenium.webdriver.firefox.extension_connection
######## selenium.webdriver.firefox.firefox_binary
######## selenium.webdriver.firefox.firefox_profile
######## selenium.webdriver.firefox.options
######## selenium.webdriver.firefox.remote_connection
######## selenium.webdriver.firefox.service
######## selenium.webdriver.firefox.webdriver
######### class
########## WebDriver(RemoteWebDriver)
########### Methods
############ __init__(self, firefox_profile=None, firefox_binary=None, timeout=30, capabilities=None, proxy=None, executable_path="wires", firefox_option=None)
############ quit
########### properties
############ firefox_profile
############ set_context
######## selenium.webdriver.firefox.__init__
####### ie
######## selenium.webdriver.ie.webdriver
######### class
########## WebDriver(RemoteWebDriver)
########### Methods
############ __init__(self, executable_path='IEDriverServer.exe', capabilities=None, port=DEFAULT_PORT, timeout=DEFAULT_TIMEOUT, host=DEFAULT_HOST, log_level=DEFAULT_LOG_LEVEL, log_file=DEFAULT_LOG_FILE)
####### opera
####### phantomjs
####### remote
######## selenium.webdriver.remote.command
######## selenium.webdriver.remote.webdriver
######### Methods
########## create_web_element(self, element_id)
- Creates a web element with the specified eleemnt_id.
########## execute(self, driver_command, params=None)
- Sends a command to be executed by a command.CommandExecutor.
########## get(self, url)
- Loads a web page in the current browser session.
########## find_element_by_id(self, id_)
- Finds an element by id
########## find_elements_by_id(self, id_)
- Find multiple elements by id.
########## find_element_by_xpath(self, xpath):
########## find_elements_by_xpath(self, xpath):
########## find_element_by_link_text(self, link_text):
########## find_elements_by_link_text(self, text):
########## find_element_by_partial_link_text(self, link_text):
########## find_elements_by_partial_link_text(self, link_text):
########## find_element_by_name(self, name):
########## find_elements_by_name(self, name):
########## find_element_by_tag_name(self, name):
########## find_elements_by_tag_name(self, name):
########## find_element_by_class_name(self, name):
########## find_elements_by_class_name(self, name):
########## find_element_by_css_selector(self, css_selector):
########## find_elements_by_css_selector(self, css_selector):

########## execute_script(self, script, *args)
- Synchronously Executes JavaScript in the current window/frame.
########## execute_async_script(self, script, *args)
- Asynchronously Executes JavaScript in the current window/frame.
########## close(self)
########## quit(self)
########## find_element(self, by=By.ID, value=None)
- 'Private' method used by the find_element_by_*methods.
- return self.execute(Command.FIND_ELEMENT, {'using':by, 'value':value})['value']
########## find_elements(self, by=By.ID, value=None)
- 'Private'
########## maximize_window(self)
########## switch_to_active_element(self)
########## switch_to_window(self, window_name)
########## switch_to_frame(self, frame_reference)
########## back(self)
########## forward(self)
########## refresh(self)
########## get_cookies(self)
########## get_cookie(self)
########## delete_cookie(self, name)
########## delete_all_cookies(self)
########## add_cookie(self, cookie_dict)
########## implicitly_wait(self, time_to_wait)
- Sets a sticky timeout to implicitly wait for an element to be found, or a command to complete.
  
########## set_script_timeout(self, time_to_wait)
########## set_page_load_timeout(self, time_to_wait)
######### Properties
########## title(self)
- Returns the title of the current page.
########## current_url(self)
########## page_source(self
########## current_window_handle(self)
########## window_handles(self)
########## switch_to(self)
######## selenium.webdriver.remote.webelement
######### class
########## WebElement(object)
- Represents a DOM element.
########### Methods
############ __init__(self, parent, id_, w3c=False)
############ __repr__(self)
############ click(self)
############ submit(self)
############ clear(self)
############ get_attribute(self, name)
############ is_selected(self)
############ is_enabled(self)
############ find_element_by_id(self, id_)
############ find_elements_by_id(self, id_)
############ find_element_by_name(self, name)
############ find_elements_by_name(self, name)
############ find_element_by_link_text(self, link_text)
############ find_elements_by_link_text(self, link_text)
############ find_element_by_partial_link_text(self, link_text)
############ find_elements_by_partial_link_text(self, link_text)
############ find_element_by_tag_name(self, name)
############ find_elements_by_tag_name(self, name)
############ find_element_by_xpath(self, xpath)
############ find_elements_by_xpath(self, xpath)
############ find_element_by_class_name(self, name)
############ find_elements_by_class_name(self, name)
############ find_element_by_css_selector(self, css_selector)
############ find_elements_by_css_selector(self, css_selector)
############ send_keys(self, *value)
- Simulates typing into the element
############ is_displayed(self)
############ value_of_css_properties
############ screenshot(self, filename)
############ __eq__(self, element)
############ __ne__(self, element)
############ _execute(self, command, params=None)
############ find_element(self, by=By.ID, value=None)
############ find_elements(self, by=By.ID, value=None)
############ __hash__(self)
############ _upload(self, filename)
########### Properties
############ tag_name(self)
############ text(self)
############ location_once_scrolled_into_view(self)
############ size(self)
############ location(self)
############ rect(self)
############ screenshot_as_base64(self)
############ screenshot_as_png(self)
############ parent(self)
############ id(self)
####### safari
####### support
######## selenium.webdriver.support.abstract_event_listener
######## selenium.webdriver.support.color
######## selenium.webdriver.support.event_firing_webdriver
######## selenium.webdriver.support.events
######## selenium.webdriver.support.expected_conditions
- generally useful within webdriver tests.
######### class
########## title_is(object)
########## title_contains(object)
- An expectation for checking that the title contains a case-sensitive substringn.
########## presence_of_element_located(object)
########## visibility_of_element_located(object)
########## visibility_of(object)
########## presence_of_all_element_located(object)
########## visibility_of_any_elements_located(object)
########## text_to_be_present_in_element(object)
########## text_to_be_present_in_element_value(object)
########## frame_to_be_available_and_switch_to_it(object)
########## invisibility_of_element_located(object)
########## element_to_be_clickable(object)
- An Expectation for checking an element is visible and enabled such that you can click it
########### Methods
############ __init__(self, locator)
############ __call__(self, driver)
########## staleness_of(object)
########## element_to_be_selected(object)
########## element_located_to_be_selected(object)
########## element_selection_state_to_be(object)
########## element_located_selection_state_to_be(object)
########## alert_is_present(object)
######### methods
########## _element_if_visible(element, visibility=True)
########## _find_element(driver, by)
########## _find_elements(driver, by)
######## selenium.webdriver.support.select
######## selenium.webdriver.support.ui
######### Select (import from .select)
######### WebDriverWait (import from .wait)
######## selenium.webdriver.support.wait
######### class
########## WebDriverWait(object)
########### Methods
############ __init__(self, driver, timeout, poll_frequency=POLL_FREQUENCY, ignored_exceptoins=None)
############ __repr__(self)
############ until(self, method, message='')
- Calls the mehod provided with the driver as an argumetn until the return value is not False.
############ until_not(self, method, message='')
####### selenium.webdriver.__init__
######## Firefox(import WebDriver from .firefox.webdriver)
######## FirefoxProfile(import from .firefox.fireprofile)
######## Chrome(import WebDriver from .chrome.webdriver)
######## ChromeOptions(import Options from .chrome.options)
######## Ie(import WebDriver from .ie.webdriver)
######## Edge(import WebDriver from .edge.webdriver)
######## Opera(import WebDriver from .opera.webdriver)
######## Safari(import WebDriver from .safari.webdriver)
######## BlackBerry(import WebDriver from .blackberry.webdriver)
######## PhantomJS(import WebDriver from .phantomjs.webdriver)
######## Android(import WebDriver from .android.webdriver)
######## Remote(import WebDriver from .remote.webdriver)
######## DesiredCapabilities(import .common.desired_capabilities)
######## ActionChains(import .common.action_chains)
######## TouchActions(import .common.touch_actions)
######## Proxy(import .common.proxy)
###### selenium.selenium
####### class
######## selenium(builtins.object)
- 
  Defines an object that runs Selenium commands
######### Element Locators
######### Element Filters
######### String-match Patterns
######### Methods
########## __init__
- __init__(self, host, port, browserStartCommand, browserURL, http_timeout=90)
########## add_CustomRequestHeader
- add_CustomRequestHeader(self, key, value)
## Selenium IDE
- Firefoxプラグイン。

## History
- [[http://blog.trident-qa.com/2013/05/so-many-seleniums/][Selenium何とかっていうツールがやたら色々あるのはどういうわけなのか - 品質向上ブログ]]

### Selenium Core
- 
  原型は、2004年に米ThoughtWorks社で働いていたJason Huggins氏により作られた社内向けツール。

### Selenium RC (Remote Control)
- 
  Selenium 1とも。
  コマンドをSeleneseという。
  
### Selenium IDE
- 
  ユーザのブラウザ操作を記録して、そこからSeleniumのスクリプトを生成するFirefoxプラグイン。
  
### WebDriver
- 
  2006年、GoogleのSimon Stewartが開発着手。
  ブラウザ操作をJavaScriptでなく、ブラウザの拡張機能やOSネイティブの機能を使って行う仕組み。
  そのためSelenium Serverのような中継サーバも不要となる。

- https://w3c.github.io/webdriver/webdriver-spec.html

### Selenium WebDriver
- 
  2011/7, Selenium RCとWebDriverを統合したもの。
  どちらのコマンドも使えるが、WebDriverのコマンドが優れているので、そちらを利用するのが良い。
  Selenium 2 とも。
### Selenium Builder
- 
  Firefox拡張。
  Selenium IDEはSelenium RCの機能しか利用できないので、
  Selenium WebDriverの機能を利用できるSelenium Builderの開発が活発。

## Driver
### ChromeDriver
- https://sites.google.com/a/chromium.org/chromedriver/downloads
## Memo
### JSON Wire Protocol
- [[https://code.google.com/p/selenium/wiki/JsonWireProtocol][The WebDriver Wire Protocol - selenium]]

### pip installed
- Python/Lib/site-packages/selenium
### submit, send_keys, click
- click()でうまく行かない場合は、send_keys(Key.RETURN)などを使う。
  submit()はフォーム中であれば任意の場所で実行してくれる。
  submitのボタンを探してきてclick()をしても同様の動きとなる。
### 複数のクラスを条件として選択
- 複数のクラスを条件とするには、xpathかcssSelectorを使うとよい、とのこと。
  https://teratail.com/questions/90876
### ファイルをアップロードする
- クリックしてポップアップを開くのではなく、'input type="file"'のタグにsendKeysで直接ファイル名を指定する。
  [[http://www.dafuku.com/2014/12/selenium-file-upload.html][Seleniumでファイルがアップロードできない時の対処法 - ダーフク.com]]
## Page Memo
### Selenium with Python
- [[http://selenium-python.readthedocs.io/#][Selenium with Python]]
#### Installation
- pip install selenium
#### Getting Started
- import
  from selenium import webdriver
  from selenium.webdriver.common.keys import Keys

- driver open & close
  driver = webdriver.Firefox()
  driver = webdriver.Chrome()

  driver.close()

- page
  driver.get("url")

- find
  elem = driver.find_element_by_name("q")

- operation
  elem.clear()
  elem.send_keys("pycon")
  elem.send_keys(Keys.RETURN)
#### Navigating
- find
  elem = dviver.find_element_by_id("passwd-id")
  elem = dviver.find_element_by_name("passwd")
  elem = dviver.find_element_by_xpath("//input[@id='passwd-id']")

- fill forms
  elem = dviver.find_element_by_xpath("//select[@name='name']")
  all_options = elem.find_elements_by_tag_name("option")
  for optoin in all_options:
      print()
      option.click()

- Select
  from selenium.webdriver.support.ui import Select
  select = Select(driver.find_elemnt_by_name('name'))
  select.select_by_index(index)
  select.select_by_visible_text("text")
  select.select_by_value(value)
  
  select.deselect_all()

- Drag and Drop
  from selenium.webdriver import ActionChain
  ActionChains(driver).drag_and_drop(elem, target).perform()

- Moving between windows and frames

- Popup dialogs
  driver.switch_to_alert()

- Navigation
  driver.forward()
  driver.back()

- Cookies
  cookie = {'name' : 'foo', 'value' : 'bar'}
  driver.add_cookie(cookie)
  driver.get_cookies()

#### Location Elements
- locate
  find_element_by_id
  find_element_by_name
  find_element_by_xpath
  find_element_by_link_text
  find_element_by_partial_link_text
  find_element_by_tag_name
  find_element_by_class_name
  find_element_by_css_selector
  (if you want to find multipleelements, use find_element"s"_by~, like "find_elements_by_name")

#### Waits
- Explicit Waits
  from selenium.webdriver.support.ui import WebDriverWait
  from selenium.webdriver.support import expected_conditions as EC
  
  try:
      elem = WebDriverWait(driver, 10).until(
          EC.presence_of_element_located((By.ID, "myDynamicElement"))
      )
  finally:
      driver.quit()

  - Conditions
    title_is
    title_contains
    presence_of_element_located
    visibility_of_element_located
    visibility_of
    presence_of_all_elements_located
    text_to_be_present_in_element
    text_to_be_present_in_element_value
    frame_to_be_available_and_switch_to_it
    invisibility_of_element_located
    element_to_be_clickable
    staleness_of
    element_to_be_selected
    element_located_to_be_selected
    element_selection_state_to_be
    element_located_selection_state_to_be
    alert_is_present

    - Custom Wait Conditions

- Implicit Waits
  poll the DOM for a certain amount of time when trying to find any element (or elements) not immediately available.
  Once set, the implicit wait is set for the life of the WebDriver object.
  
  driver.implicitly_wait(10) # seconds
  
#### Page Objects
#### WebDriver API
#### FAQ
### SeleniumHQ
- http://www.seleniumhq.org/docs/03_webdriver.jsp
## Link
- [[http://www.seleniumhq.org/][SeleniumHQ]]
- [[https://app.codegrid.net/entry/selenium-1][入門、Selenium - CodeGrid]]

- [[https://seleniumhq.wordpress.com/2016/10/13/selenium-3-0-out-now/][Selenium 3.0: Out Now! - Official Selenium Blog]]

- https://www.kaitoy.xyz/2017/07/12/2017-selenium-headless-browsers/
### API
- [[http://stackoverflow.com/questions/5644868/webdriver-selenium-2-api-documentation][WebDriver (Selenium 2) API documentation - stackoverflow]]

### Python
- [[http://selenium-python.readthedocs.io/#][Selenium with Python]]
- [[http://seleniumhq.github.io/selenium/docs/api/py/api.html][Selenium Documentation (Python)]]
