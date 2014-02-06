## Description

Prevent single Dynos on Heroku to idle

## Usage

1. Clone the project:
   * ```git clone https://github.com/drobakowski/wake-up-dyno.git && cd wake-up-dyno```

2. Configure the names of the dynos you want to prevent to idle:
   * ```vi bin/wake-up-dyno.config```
   * Commit your the changes:
```git commit -m "Configured some dynos to wake" bin/wake-up-dyno.config```

3. Add the Heroku buildpack as described at [Heroku buildpack](https://github.com/cstar/heroku-buildpack-chicagoboss):
   * ```heroku create --buildpack "https://github.com/archaelus/heroku-buildpack-erlang.git"```

4. Deploy your code to Heroku:
   * ```git push heroku master```

5. Open the Heroku app dashboard
   * Go to the resource settings of the new created app and click 'Get Add-ons'
   * Search for the 'Heroku Scheduler' and add the free standard plan to your app
   * Go back to your shell and execute:
```heroku addons:open scheduler```
   * Click 'Add Job...' and set ```wake-up-dyno``` as the task to execute hourly

6. Check if everything works properly
   * Run:
```heroku run bash```
   * Execute:
```./bin/wake-up-dyno``` and check the console output for errors


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/drobakowski/wake-up-dyno/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

