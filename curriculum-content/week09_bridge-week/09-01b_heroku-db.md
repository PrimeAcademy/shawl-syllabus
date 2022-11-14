# Deploy Heroku App with Database (Using bit.io)

[Heroku](https://www.heroku.com/) is a Cloud Application Platform that will allow you to publish your apps to the web. We'll be primarily using Heroku in this class but it's important to note that there are many other companies out there that offer similar services.

Best of all, [Heroku](https://www.heroku.com/) is free for development use! 

## Summary Steps

### Heroku Prerequisite

1. Sign up for an account on [Heroku.com](https://www.heroku.com/)
2. Install Heroku CLI by typing `brew tap heroku/brew && brew install heroku` in Terminal
  - [Additional installation notes and troubleshooting](https://devcenter.heroku.com/articles/heroku-cli#download-and-install)
3. Authenticate by typing `heroku login` in Terminal

> Note: Your project also needs to have a git repository.

### Heroku Setup

Before you deploy, make sure your server `PORT` is configured correctly as:

```JavaScript
const PORT = process.env.PORT || 5000;
```

Run the following commands from within your project folder.

1. In terminal, navigate to your project folder and type `heroku create`
2. Login in if prompted
3. Type `git remote -v` to ensure it added successfully
4. In terminal, type `git push heroku main`
5. Our website is now live! However... we also have a database

### PostgreSQL on Heroku

We're going to use bit.io for the database of this deployed app. This site will host our database, aka our database server - it will listen for database requests and respond appropriately, while storing our data. And it's free!

1. Sign up for an account if you have not already done so.
2. Create a new database, ideally using the same name as your local database.
3. Copy your `CREATE TABLE` statements and any dummy data from your database.sql file into the bit.io Query Editor for the current database. Run 'em.
4. Link your deployed Heroku app to your newly created bit.io database:
  a. On bit.io, within the current project's database, click the 'Connect' button near the top of the screen (next to the 'Data' button); copy the value for 'Postgres Connection' (should begin with 'postgresql://').
  b. On your Heroku Dashboard, select the current project. Click 'Settings' near the top of the screen, then scroll down to the 'Config Vars' section. Click 'Reveal Config Vars.' Type `DATABASE_URL` into the text input with the placeholder "KEY," and paste the value you just copied on bit.io into the text input with the placeholder "VALUE." Click "Add."
5. Update your server-side Javascript so your pg `pool` is configured to connect to your bit.io database when the app is running on Heroku, and your local Postgres database when the app is running locally.

**modules/pool.js**

```JavaScript
const pg = require('pg');
let pool;

// When our app is deployed to the internet 
// we'll use the DATABASE_URL environment variable
// to set the connection info: web address, username/password, db name
// eg: 
// DATABASE_URL=postgresql://jDoe354:secretPw123@some.db.com/prime_app
if (process.env.DATABASE_URL) {
    pool = new pg.Pool({
        connectionString: process.env.DATABASE_URL,
        ssl: {
            rejectUnauthorized: false
        }
    });
}
// When we're running this app on our own computer
// we'll connect to the postgres database that is 
// also running on our computer (localhost)
else {
    pool = new pg.Pool({
        host: 'localhost',
        port: 5432,
        database: 'prime_feedback', 
    });
}

module.exports = pool;
```

When you need a pool, use the following code:

```JavaScript
let pool = require('../modules/pool');
```

Next, commit your changes and push them to Heroku:

```
git add .
git commit -m "MESSAGE"
git push heroku main
```

> Note: You'll need to commit and push each time you make a change that you want to deploy to Heroku. Automatic deployments are covered in [a later section](#gui-and-automatic-deployment) **Keep in mind you CAN NOT pull from Heroku. This is not a replacement for GitHub!**

Lastly, open terminal and type `heroku open`, which should show you your deployed site!

> Note: It is best to fully test your code locally before deploying to Heroku. Bugs are much harder to troubleshoot on a live website!

### Miscellaneous

- `heroku logs` - Display error logs
- `heroku config` - Show basic app info
- `heroku restart` - Sometimes it helps to turn things off an on again
- `heroku open` - Opens the website for you project in the browser

## GUI and Automatic Deployment

The [Heroku](https://www.heroku.com/) website GUI can simplify several of the steps taken above especially for projects where you intend to make future changes.

1. In [your list of Heroku apps](https://dashboard.heroku.com/apps), select your application.
2. Under the `Deploy` tab, in the `Deployment Method` section, select `Github`. Connect to the `Github` repository with your application by searching for the name of your repository.
3. In the `Manual Deploy` section, click `Deploy Branch` to deploy for the first time.

## Connect Postico to your bit.io Database

If you would like to edit your deployed app's database directly from Postico, you can connect to your bit.io database via a new Favorite Postico connection. 

1. On bit.io, within the current project's database, click the 'Connect' button near the top of the screen (next to the 'Data' button).
2. Open Postico and select `New Favorite`.
3. In the new Postico favorite, update the following to match Heroku:
  - Host
  - User
  - Database
  - Password
  - Port
4. Click `Connect` and you should have access to your database directly from Postico!

## Resources

More detailed instructions can be found [in the Heroku docs](https://devcenter.heroku.com/articles/git)