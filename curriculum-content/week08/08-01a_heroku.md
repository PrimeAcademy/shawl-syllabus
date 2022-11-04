# Heroku

[Heroku](https://www.heroku.com/) is a Cloud Application Platform that will allow you to publish your apps to the web. We'll be primarily using Heroku in this class but it's important to note that there are many other companies out there that offer similar services.

Best of all, [Heroku](https://www.heroku.com/) is free for development use! 

## Summary Steps

### Heroku Account Sign Up (one time)

To use heroku, you will need to sign up for an account on [heroku.com](https://www.heroku.com/).

Heroku requires _Multi Factor Authentication_ (MFA) for all accounts. MFA is a security measure that uses your phone (or other device) to prove that you are who you say you are. A common example is when apps send you a text message with a one-time code to login.

During the sign-up process on [heroku.com](https://www.heroku.com/) you will be asked to setup MFA (if not, go to _Account Settings > Setup MFA_):

- Select _Salesforce Authenticator_ as your verification method.
- Install the _Salesforce Authenticator_ app on your phone
- Open the phone app, and select _Add an Account_
- The app will display a two word phrase. Type this phase into the heroku web site when prompted.
- Log out of heroku and log back in, to confirm that MFA is setup properly.

Your heroku account is now configured to use MFA. Whenever you login to heroku, you will receive a push notification asking you to approve the login.

> These things tend to change periodically. Heroku's own documentation may help if the above isn't working as expected. https://devcenter.heroku.com/articles/multi-factor-authentication

### Heroku CLI Setup (one time)

#### brew
1. Install Heroku CLI by typing `brew tap heroku/brew && brew install heroku` in Terminal
2. Authenticate by typing `heroku login` in Terminal

OR
#### npm (likely better for m1)
1. Install Heroku CLI by typing `npm install -g heroku` in Terminal
2. Authenticate by typing `heroku login` in Terminal

### Create a Heroku project

From your terminal, `cd` into your project directory. Note that your project must be setup as a git repository for these commands to work.

Run the following commands from within your project folder.

1. `heroku create`
2. Login in if prompted -- it might ask to open a browser
3. Type `git remote -v` to ensure it added successfully. You should see a remote called `heroku`

Make sure your PORT is configured correctly as:

```JavaScript
const PORT = process.env.PORT || 5000;
```

This will allow heroku to tell your app which port to listen on.

Next, commit your changes and push them to Heroku:

```
git add .
git commit -m "MESSAGE"
git push heroku main
```

   > Note: You'll need to commit and push each time you make a change that you want to deploy to Heroku. **Keep in mind you CAN NOT pull from Heroku. This is not a replacement for GitHub!**

Lastly, open terminal and type `heroku open` as a shortcut to open your website in a browser.

   > Note: It is best to fully test your code locally before deploying to Heroku. Bugs are much harder to troubleshoot on a live website.

### Miscellaneous

- `heroku logs` - Display error logs
- `heroku config` - Show basic app info
- `heroku restart` - Sometimes it helps to turn things off an on again
- `heroku open` - Opens the website for you project in the browser

## Resources

More detailed instructions can be found here: 

- [https://devcenter.heroku.com/articles/git](https://devcenter.heroku.com/articles/git)
