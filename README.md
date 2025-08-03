<h1 align="center">  <img src="https://avatars.githubusercontent.com/u/1119453?s=200&v=4" width="60" height="60" > <a href="https://github.com/BrowserStackCE/browserstack-webdriverio-appium-cucumber">BrowserStack Examples Appium WebdriverIO Cucumber</a>  <img src="http://v4.webdriver.io/images/webdriverio.png" width="60" height="60" ></h1>


Welcome to BrowserStack WebdriverIO Cucumber Examples, a sample UI testing framework empowered with Appium, Webdriverio, Cucumber. Along with the framework the repository also contains test scripts written for BrowserStack Demo Application.

This repository includes a sample configuration setup to run tests on BrowserStack platforms, including mobile devices through App Automate.
## 🛠️ Setup

### Step 1: Upload your app to BrowserStack

Upload the `.apk` and `.ipa` files to [BrowserStack App Automate](https://www.browserstack.com/app-automate) and note the **app URL/hash**.

You can upload your application on our platform using one of the following options:

1. You can upload an application on BrowserStack from the [BrowserStack App Automate Dashboard](https://www.browserstack.com/app-automate) directly using the upload app option at the top.

2. You can also use the below API to upload an application:  
```bash
curl -u "<username>:<access_key>" \
-X POST "https://api-cloud.browserstack.com/app-automate/upload" \
-F "file=@/path/to/app/file/application-debug.ipa"
```

Note: Please replace the username, access key, and path to the application. (Please don't remove the @ in the path)
For reference: https://www.browserstack.com/docs/app-automate/api-reference/appium/apps#upload-an-app

Sample APK path: ```android/app/WikipediaSample.apk```

Sample IPA path: ```ios/app/BStackSampleApp.ipa```

### Step 2: Update config

Update the app hash in:

- `android/configs/wdio.browserstack.*.conf.js`
- `ios/configs/wdio.browserstack.*.conf.js`

### Step 3: Install dependencies

**For Android**
```bash
cd android
npm install
```
**For iOS**
```bash
cd ios
npm install
```
# Run Tests
- Android
``` bash
# Inside /android

# Run tests on BrowserStack Local
npm run test:local

# Run tests using public app URL
npm run test:single

# Run tests in parallel
npm run test:parallel
```
- iOS
``` bash
# Inside /ios

# Run tests on BrowserStack Local
npm run test:local

# Run tests using public app URL
npm run test:single

# Run tests in parallel
npm run test:parallel
```
# Browserstack Test Observability

Test Observability is a reporting tool that helps you isolate the genuine test failures after eliminating noise from flaky and always failing tests and also helps with root cause analysis of failed tests.

With Test Observability, you can not only complete your run verification in minutes, you will also be empowered with rich historical data to understand the overall health of your test suites, uncover burning issues impacting the stability of your tests, and help you optimize your tests. 

You can learn more about [what the product has to offer and why you should be using it](https://www.browserstack.com/docs/test-observability/overview/what-is-test-observability).

Please add the following code snippet to your **wdio.conf.js**.
```js
services: [
        ['browserstack', {
            testObservability: true,
            testObservabilityOptions: {
                'projectName': 'Specify your project name here. It should not be dynamic',
                'buildName': 'Specify your job name here. For e.g. `Nightly regression`. It should not be dynamic',
                'buildTag': 'Any build tag goes here. For e.g. commit message'
            },
        }]
    ],
```
To get started with the Test Observability integration with your WebdriverIO Project, please refer to this [documentation](https://www.browserstack.com/docs/test-observability/quick-start/webdriverio).
