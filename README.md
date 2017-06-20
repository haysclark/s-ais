sAIS
====
[![Build Status](https://travis-ci.org/infinitedescent/s-ais.svg?branch=develop)](https://travis-ci.org/infinitedescent/s-ais) [![Coverage Status](https://coveralls.io/repos/github/infinitedescent/s-ais/badge.svg?branch=develop)](https://coveralls.io/github/infinitedescent/s-ais?branch=develop) [![Known Vulnerabilities](https://snyk.io/test/github/infinitedescent/s-ais/badge.svg)](https://snyk.io/test/github/infinitedescent/s-ais)

> Server-AIS self-reporting service for DeLorme inReach/Explorer devices

sAIS is a web service for updating the AIS position of a vessel on [MarineTraffic.com](https://www.marinetraffic.com/) with the Satellite tracking data from a [DeLorme device](http://info.delorme.com/) when out of range of terrestrial AIS receiving stations.  The service is configured to run every 10 minutes on a free [Heroku](https://www.heroku.com) account.  During that period, if no positional updates occurred from AIS receiving stations, the service will send a [self-report](https://www.marinetraffic.com/en/p/report-your-own-position), which gives ample time for the more frequent AIS receiving stations which typically report every minute.

This software is authored as an alternative for recreational mariners to promote cruising and share their adventure without having to invest in costly satellite tracking systems intended for commercial fleets, nor costly Satellite Internet connectivity.  Please donation to help ensure the maintenance and improvements of sAIS.

> Infinite Descent, creator of sAIS has NO affiliation with Garmin DeLorme, MarineTraffic, nor Heroku.

Install
-------
Individuals interested in a help setting up a sAIS instance should contact Infinite Descent for more information.

#### Requirements
- valid Maritime Mobile Service Identity (MMSI)
- Garmin DeLorme inReach, Explorer, or other device with Sharing enabled.
- Heroku account for hosting the sAIS service.

#### Deploy sAIS
sAIS is designed to be incredibly easy to setup and run, just click on the *Deploy to Heroku* button to start the process. The link will navigate you to Heroku.com and starts the 'Create a New App' process.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/infinitedescent/s-ais/tree/develop)

- We recommend an 'App Name' of ```server-ais```.
- Fill out the critical data, in the _Config Variables_ section, make sure to read the _description_ for each value if unclear.
- When ready, press the 'Deploy' button to finish the deployment process.

#### Configure Heroku Scheduler
> Due to a limitation with the _Heroku Scheduler Add-on_, this last step **MUST** be done manually.

- In your _Heroku_ account, navigate to your 'Personal Apps' and select your new 'server-ais' application.
- From the 'Overview' tab, click on the 'Heroku Scheduler' link in the 'Configure Add-ons' section, which will open a new tab for editing the Heroku Scheduler add-on.
- Click the 'Add new job' button, which will open a dialog box.
- In the textfield enter this command: ```node bin/sync```
- Set the 'FREQUENCY' drop down to 'Every 10 minutes.'
- Click the 'Save' button to complete setup.

sAIS is now completely setup!

Verify setup
----------------
To verify sAIS is running correctly you will need to be out of any AIS receiving stations. On MarineTraffic.com, in the 'Detailed View' for your vessel, check the 'Latest Position' area. After the 'AIS Source:' you should see 'SELF' instead of an AIS station number.

Usage
-----
> Make sure you have read the MarineTraffic Disclaimer and Terms of Service.

#### sAIS Disclaimer
sAIS is free and has NO guaranty that it will not incur Heroku charges; however, the chances of this are improbable.  The application is designed to use as little processing power as possible, and the application sleeps the majority of the time, only waking up every 10 minutes to check on your location.  However, this website does wake up your Heroku instance and uses a small amount of CPU time each time the website is accessed, so avoid navigating to the App or sharing the URL with others.  Remember, there is no reason to revisit this site other then to check if S-AIS is still functioning.

License
-------
GPL-3.0 © 2017 - [Infinite Descent, LLC](http://infinitedescent.com)
