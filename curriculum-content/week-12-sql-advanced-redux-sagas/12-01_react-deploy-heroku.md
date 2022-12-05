# Full Stack Create-React-App on Heroku

There are some special steps to ensure your React app can be accessed on heroku!
This does not replace the existing instructions -- rather this is an addon!

## package.json


### Start Script

Make sure the `start` script in your `package.json` starts your node server and not React.

`"start": "node server/server.js",`

### Build Script

Make sure your `package.json` contains a `build` script:

`"build": "react-scripts build"`


## Git Commit

`git add .`
`git commit -m "YOUR COMMIT MESSAGE"`

## Git Push
Push to heroku `git push heroku main`

Heroku will automatically run `npm run build`, which will make a production build of your code.
After that, heroku will run `npm start`, which will start node.
