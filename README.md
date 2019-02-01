## Project 1

In our first project, you'll get a server up and running, and write and deploy some React-based code using a node.js server. (OMG what does that all mean?)

The goals are:
- Get comfortable with the command line.
- Get experience with Google Cloud Platform.
- Build on knowledge of HTML/CSS.
- Learn basics of the React front-end library.
- Learn how web *browsers* interact with web *servers*.
- Learn how to save data.

### Week 1

This week, we'll spend most of our time getting your server running in the cloud, exploring the command line, and tweaking an existing React app.

#### Getting your (free!) server on Google Cloud Platform.

Sign up for a [Google Cloud Platform account](https://console.cloud.google.com/). You'll need to enter a credit card to prove you're human, but you won't be charged.

Create a new project, then navigate to `Compute Engine` > `VM Instances` and create a new VM. You'll want to use these settings to make sure it's free! Pick your own name, though, obviously. (You may need to create a "project" for this.)

![creating an instance](img/creating-an-instance.png)

Once you've created your instance, you'll need to open a specific `port` to allow our development server to be publicly accessible on the internet. To do that, navigate to `VPC Network` > `Firewall Rules` and click on `Create Firewall Rule`. Use these settings:

![new firewall rule](img/create-firewall-rule)

With these done, go back to `Compute Engine` > `VM Instances` and Start your VM instance. Once it's running, you can connect to it with the `SSH` link. It'll open a terminal where you can issue commands.

Run this first command:

`curl -sL https://zamfi.net/img/cp2_setup.sh | bash -`

Copy and paste it from above, don't try to type it in -- it has weird characters like the vertical bar (pipe) `|` in it!

This will take a little while as it installs a bunch of dependencies and creates a new react project for you. While it's installing, take a look at this [list of command line tools](https://files.fosswire.com/2007/08/fwunixref.pdf).

Change into the `hello-world` directory (using `cd hello-world`) and run `npm start`. After a couple of minutes, you should see some "complation succeeded" text with what looks like a URL. That URL won't work -- because you're not on the same local network as your server. Instead, copy the `External IP` from the VM instances page, open up your web browser, and visit *your-ip*`:3000`. For my instance, this was `35.227.190.43:3000` -- you should see a React logo!

#### Replacing the generic React starter app

Once you get to this point, open a second terminal window by clicking on `SSH` again. In this terminal, use the `nano` program to edit the file `src/App.js`. Add some text about yourself! Format it nicely, and show us your new CSS chops by styling through `src/App.css`.

Next, you'll replace the generic React server app with the code from [wishing-well](http://github.com/zamfi/wishing-well), our real starting point for Project 1! Copy the contents of wishing-well's `src/App.js` and `src/App.css` into your project.

#### Extending the wishing well

Make the following changes to the wishing well:

- Add a bunch of new wisdoms.
- Create a “new” button that triggers the `addWisdom` function. There's already CSS for this button in `src/App.css` in a class called `new-wisdom`.
- Ensure a new, different wisdom shows up every time you click. You could guarantee this by cycling from one wisdom to the next. Or by checking to make sure that the new randomly selected wisdom is "different" from the old one.
- Make the wisdom change every 15 seconds on its own, even if you don't click the button. (The `setInterval` function might be useful here!)

Challenges (optional):
- Create a new array of attributions, and display a random attribution for each piece of wisdom.
- Make the wisdoms show up cumulatively in a list. Do some research on how to display a list in React. Then don’t show more than 3 at a time!

Finally:
- Make it your own! Reimagine the wishing well on your own in some way. Give it some whimsy, or a new look. Whatever appeals to you!
