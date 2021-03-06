<img src="https://openlittermap.com/assets/logo_small.png" />
<h3>About OpenLitterMap</h3>
<hr>
<p>OpenLitterMap is an open, interactive, and accessible database of the world's litter and plastic pollution.</p>
<p>We are building a fun data-collection experience to harness the unprecedented potential of citizen scientists around the world.</p>
<p>We believe that science on pollution should be an open, transparent and democratic process- not limited or controlled by anyone or any group.</p>
<p>If you would like to help shape the future of OpenLitterMap, we would love to have you in our <a href="https://join.slack.com/t/openlittermap/shared_invite/zt-fdctasud-mu~OBQKReRdC9Ai9KgGROw">Slack Channel</a></p>
<p>Every Thursday, 6pm Irish time, we run a community zoom call for ~1 hour where anyone interested in OpenLitterMap can listen in to learn more, and share ideas to help the future direction of the platform.</p>
<p>OpenLitterMap is underdeveloped, but we are a community of over 3,600 contributors who have crowdsourced more than 100,000 uploads from 80 countries.</p>
<p>All of our data is available to explore on the <a href="https://openlittermap.com/global">Global Map</a> and more sophisticated <a href="https://openlittermap.com/world/The%20Netherlands/Zuid-Holland/Wassenaar/map">"city grid maps"</a> are also available to explore. Anyone can download all of our data for free.</p>
<hr>
<p>We have just launched a <a href="https://www.gofundme.com/f/openlittermap-a-revolutionary-app-to-map-litter">GoFundMe</a> which includes our first promotional video and a new demo video showing how to use our app.</p>
<p>The source code for the mobile app (React Native) will launch soon, followed by the OpenLitterAI and our smart contacts.</p>
<p>OpenLitterMap is the first project to reward users with cryptocurrency for the production of geographic information. By using the app and doing "proof of work", users are "mining" Littercoin which we are experimenting with to reward and incentivize the sharing of geospatial data on plastic pollution.</p>
<br>
<p>STAY TUNED FOR LOTS OF EXCITING UPDATES</p>
<hr>
<p>OpenLitterMap-web is built with <a href="https://laravel.com">Laravel</a>, <a href="http://vuejs.org/">Vue.js</a> and <a href="https://bulma.io">Bulma</a></p>
<p>1. Download and install <a href="https://www.virtualbox.org/wiki/Downloads">Virtual box</a> which will give you a Virtual Machine. This is used to give us all the same development environment. Alternatively, if you use mac, you can use <a href="https://laravel.com/docs/5.8/valet">Laravel Valet</a></p>
<p>2. Download and install <a href="https://www.vagrantup.com/downloads.html">Vagrant</a> which you will use to provision, turn on and shut down your VM.</p>
<p>3. Go to your command prompt or terminal and in your user root directory (C:/Users/You) run</p>  

`vagrant box add laravel/homestead`

<p>4. Clone the box by running</p> 

`git clone https://github.com/laravel/homestead.git ~/Homestead`

<p>You should now have a "Homestead" folder on your machine at C:/Users/You/~/Homestead</p>

<p>5. Cd into the Homestead directory and run the command below in terminal/command prompt. This will create a Homestead.yaml file in the homestead directory.</p>

Mac and Linux

`bash init.sh`

Windows

`init.bat`

<p>6. Open the Homestead.yaml file and update it to match the sample below</p>

```
---
ip: "192.168.10.10"
memory: 2048
cpus: 1
provider: virtualbox

authorize: ~/.ssh/id_rsa.pub

keys:
    - ~/.ssh/id_rsa

folders:
    - map: ~/Code
      to: /home/vagrant/Code

sites:
    - map: olm.test
      to: /home/vagrant/Code/openlittermap-web/public
      php: "7.3"

databases:
    - olm

...
```

<p>7. update your hosts file (located at /etc/hosts on mac/linux and C:\Windows\System32\drivers\etc\hosts on windows) and include:</p>

`192.168.10.10 olm.test`

<p>8. Download the repo and save it locally into your "Code" folder</p> 

`C:/Users/You/Code/openlittermap-web`

<p>9. When you want to boot up the VM, cd into the Homestead folder and run</p>

`vagrant up`

<p>9.1 If this is your first time installing, you need to run</p>

`vagrant provision` 

<p>10. Install npm dependencies by running the command below in C:/Users/You/Code/openlittermap-web</p>

`npm install`

<p>11. SSH into the VM by running</p>

`vagrant ssh`

<p>12. To install composer run</p>

`composer install`

<p>13. Open the .env file in C:/Users/You/Code/openlittermap-web</p>

<p>13.1 Add</p>

`WEBSOCKET_BROADCAST_HOST=192.168.10.10`

<p>13.2 Go to https://dashboard.pusher.com/accounts/sign_up and sign up for an account. Now go to account/api key and click create key. Copy this key and head back over to the .env file</p>

<p>13.3. Update your PUSHER_APP_SECRET to read PUSHER_APP_SECRET=[your api key]</p>

<p>You should now be able to open the browser and visit old.test</p>

<p>You can migrate the tables with "php artisan migrate"</p>
<p>If you would like to contribute something, make a new branch locally "git checkout -b feature/my-new-feature". We would love to see your pull requests!</p>

<p>You might notice there are some websocket errors in the browser. Some operations like adding photos broadcast live events to the client. It's easy to get websockets set up to resolve this.</p>

```
In your .env file, add "WEBSOCKET_BROADCAST_HOST=192.168.10.10"
In broadcasting.php, change 'host' => env('WEBSOCKET_BROADCAST_HOST')
In one window, run `art websockets:serve --host=192.168.10.10`
Then, in another window, run `art horizon`
To test it's working, open another window. Open tinker and run event new(\App\Events\UserSignedUp(1));
```

<p>You are now ready to get started!</p>
<p>Have fun and thanks for taking an interest in OpenLitterMap</p>
