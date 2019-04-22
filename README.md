protractor-demo
===============

Demo test application and protractor tests.

Setup
-----

    git clone https://github.com/juliemr/protractor-demo.git
    cd protractor-demo
    npm install

To run
------
Get ChromeDriver set up: Run `./node_modules/.bin/webdriver-manager update`.

Start the test application server with
`node app/expressserver.js`
Or if you're feeling lazy, just `npm start`.

Run the tests with
`node_modules/.bin/protractor test/conf.js`
Or if you're feeling lazy, just `npm test`.

Watch them go!

Run with Docker
------
Build image
`docker build -t <your username>/protractor-demo-app .`

Run the image
`docker run -p 49160:3456 -d <your username>/protractor-demo-app`

`docker run -d --restart always --name protractor-demo-app -p 49160:3456 paulcosma/protractor-demo-app`

