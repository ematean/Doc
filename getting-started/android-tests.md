---
description: setting up an Android Test
---

# Android Tests

## Prerequisite

* [Install Java JDK and Maven](https://docs.autonomx.io/prerequisites)
* [Setup Android Environment](https://docs.autonomx.io/prerequisites/android)

## Run Setup

* Run autonomx -&gt; setup.sh/.bat
  * 

![](../.gitbook/assets/image%20%2877%29.png)

## Configure Android app

* resources -&gt; properties -&gt; android.property
* ```text
  # Android
  android.app = "selendroid.apk"
  android.appDir = "resources/"
  android.mobile = "Pixel_2_XL_API_25"
  android.tablet = "Pixel_2_XL_API_25"

  # to add additional capabilities, add capability after the "android.capabilities." prefix
  # Espresso or UiAutomator2
  android.capabilties.automationName = UiAutomator2
  android.capabilties.deviceName = Android
  android.capabilties.unicodeKeyboard = true
  android.capabilties.resetKeyboard = true
  android.capabilties.fullReset = false
  android.capabilties.noReset = false
  android.capabilties.recreateChromeDriverSessions = true
  android.capabilties.autoGrantPermissions = true
  android.capabilties.newCommandTimeout = 300
  android.capabilties.noSign = true

  android.home = ""
  android.javaHome = ""
  ```
* * Example project: autonomx ▸ ⁨automation⁩ ▸ ⁨src⁩ ▸ ⁨main⁩ ▸ ⁨java⁩ ▸ ⁨modules⁩ ▸ androidApp⁩
  * Setup locators

    androidApp ▸ MainPanel.java
* {% code title="Main.java" %}
  ```text
      // Locators
      //--------------------------------------------------------------------------------------------------------    
      public static class elements {
          public static EnhancedBy REGISTER_PANEL = Element.byAccessibility("startUserRegistrationCD", "registration button");
          public static EnhancedBy POPUP_BUTTON = Element.byAccessibility("showPopupWindowButtonCD", "popup button");

      }
  ```
  {% endcode %}

## Define actions

* androidApp ▸ MainPanel.java
* {% code title="Main.java" %}
  ```text
      // Actions
      //--------------------------------------------------------------------------------------------------------    
      public void selectRegisterPanel() {
          Helper.clickAndExpect(elements.REGISTER_PANEL, RegistrationPanel.elements.USERNAME_FIELD);
      }
  ```
  {% endcode %}

## Write Test

* ⁨automation-client⁩ ▸ ⁨automation⁩ ▸ ⁨src⁩ ▸ ⁨Test ▸ ⁨java⁩ ▸ ⁨module ▸ ⁨android -&gt; tests
* setup the android driver
* {% code title="RegisterUserTest.java" %}
  ```text
      public void beforeMethod() throws Exception {
          setupWebDriver(app.androidApp.getAndroidMobileDriver());
      }
  ```
  {% endcode %}
* Add Test

```text
  public class RegisterUserTest extends TestBase {
  
  @BeforeMethod
  public void beforeMethod() throws Exception {
      setupWebDriver(app.androidApp.getAndroidMobileDriver());
  }

  @Test
  public void registerUser() {
      CommonUser user = Data.common.commonuser().withDefaultUser();

      TestLog.When("I select the registration panel");
      app.androidApp.main.selectRegisterPanel();

      TestLog.When("I register a user");
      app.androidApp.registration.registerUser(user);
  }
```

