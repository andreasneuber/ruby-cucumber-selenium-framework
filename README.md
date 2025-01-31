#  ruby-cucumber-selenium-example
Example of using Ruby with Cucumber and Selenium WebDriver for automated UI tests.

## Application under test
The feature files, step definitions and page objects were written for https://github.com/andreasneuber/automatic-test-sample-site.
Readme in that repo has further details how to set it up.

## Project setup

1. On Windows install Ruby as outlined here: https://rubyinstaller.org/

2. Install also bundler: https://www.geeksforgeeks.org/how-to-install-ruby-bundler-on-windows/

3. Make sure ChromeDriver is installed on your system (see also FAQ below)

4. Clone project

```
git clone https://github.com/andreasneuber/ruby-cucumber-selenium-framework.git
```

5. Install required dependencies

```shell
bundle install
```

## Run tests locally

```shell
# all at once..
cucumber

# or

cucumber features/AdminPrivileges.feature

# or 

cucumber features/ConvertCelsius.feature

# or

cucumber features/Creditcard.feature

# or

cucumber features/Login.feature

# or

cucumber features/ProvideYourDetails.feature

# or

cucumber features/ConcurrentWindows.feature
```

## Run all tests locally, create HTML report
Bash: 
`export now=$(date +"%Y-%m-%d_%H-%M-%S") && cucumber -f pretty -f html -o reports/$now.report.html`

PowerShell:
`$now = "reports/" + ((Get-Date).ToString('yyyy-MM-dd_hh-mm-ss') | Out-String).Trim() + ".report.html"; cucumber -f pretty -f html -o $now`


Report will appear in directory `reports` where it can be opened in a browser.

## Update Gem files
```shell
bundle update
```

## FAQ
### How to install/update Chromedriver on Windows?
There is different ways, one possibility:
1. Go to https://googlechromelabs.github.io/chrome-for-testing/ > Channel 'Stable'
2. Download the win32 or win64 version
3. Save `chromedriver.exe` somewhere in your file system
4. Edit environment variables > System Variables > Path and path to your Chromedriver location
5. If necessary restart machine
6. To check if all is good with cmd `chromedriver -version` which should give you the correct version number
7. Put file `update_chromedriver.sh` into the folder where `chromedriver.exe` is located
8. To update Chromedriver: `bash update_chromedriver.sh`
9. This should download the latest Chromedriver

### How to switch to headless mode?
Please have a look at `features\support\env.rb`, lines 5 ff.

### Is there a Docker container which has the latest Chrome browser and Chrome driver?
Please have a look here: https://hub.docker.com/u/selenium > `selenium/standalone-chrome`