# HTML Report

## Extent Reports

* Extent report is used for html reporting
* Layout:
  * Test classes are displayed as "Features"
  * Test methods are displayed as "Scenario"
  * Both test class and test method are separated by upper case letters or underscore characters
    * eg. verifyLoginTest class becomes "Verify Login Test"
    * eg. validate\_User\_Login becomes "Validate User Login"

![](../.gitbook/assets/image%20%283%29.png)

## Test Failures

* Test failures are displayed with stack trace of the failed test
* 
![](../.gitbook/assets/image%20%2836%29.png)

* A new side menu option will also be displayed 
* We will be able to see the list of failures

![](../.gitbook/assets/image%20%2826%29.png)

## Configuration

### Launch After Test

* We can enable the test report to launch in the browser automatically after the test run by enabling "report.launchRepotAfterTest" option at [Ui Testing Properties](https://ehsan-matean.gitbook.io/automationcore/~/edit/drafts/-L_QoVcSBVDLeifUW6pF/configuration/properties) located at automation-client⁩ ▸ ⁨automation⁩ ▸ ⁨resources⁩ ▸ properties.property
* ```text
  # report options
  report.launchReportAfterTest = false
  ```

### Detailed Report

* We can enable to disable the sub steps in the repot and only leave the Gherkin style comments
* ```text
  report.enableDetailedReport = false
  ```

![](../.gitbook/assets/image%20%2828%29.png)

## Test Report Location

* Test report location is displayed at the end of the test in the test console
* 
![](../.gitbook/assets/image%20%289%29.png)
