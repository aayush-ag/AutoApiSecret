AutoApi series: AutoApi, AutoApiSecret, AutoApiSR, AutoApiS

Top
This project is based on the assumption that the original tutorial can call the api correctly , and the core is the py script of paran/shadow.
This project just provides an automatic, free, and no additional equipment-free script running method, in other words, borrow a github computer/server to work . (Because the original tutorial requires a server/extra-long running equipment, most people do not have it, this project came into being)
The project is running relies github action service, this feature github inherent and non-private provision server, and the entire operation involves only you and github.
Please be sure to read and understand the principle description and design concept of the original tutorial .
Renewal is not guaranteed! Renewal is not guaranteed! Renewal is not guaranteed ! In other words, it just increases the possibility of renewal . Renewal is possible within 30 days before and after the expiration! ! !
If you understand and accept the above instructions, please proceed; if not, please click the X in the upper right corner of the browser.
project instruction
Use github action to automatically call API regularly and keep E5 development active.
It's free, no additional equipment/server is needed, and you don't need to worry about it after deployment.
Encrypted version, hide application id + secret, protect account security.
Special instructions/Thanks
Original tutorial blogger-shadow (kuan id-Paran): https://blog.432100.xyz/index.php/archives/50/
Normal version address: https://github.com/wangziyingwen/AutoApi
Encrypted version address (recommended): https://github.com/wangziyingwen/AutoApiSecret
Imitate the human application development version (including upgrade steps): https://github.com/wangziyingwen/AutoApiSR
Super version address: https://github.com/wangziyingwen/AutoApiS
Common errors and solutions/update log : https://github.com/wangziyingwen/Autoapi-test
Get the refresh_token widget from the web page (not recommended): https://github.com/wangziyingwen/GetAutoApiToken
Video tutorial: (I operate very slowly, double speed/fast forward by myself)
Online/download address: https://kino-onemanager.herokuapp.com/Video/AutoApi%E6%95%99%E7%A8%8B.mp4?preview
Station B: https://www.bilibili.com/video/av95688306/
the difference
Normal version (deprecated) : the key is exposed, you can use it if you don’t care

Encrypted version (recommended) : Apply id secret encryption to hide, improve security

Imitate the artificial application development version (semi-abandoned) : As the name implies, an upgraded version of the encrypted version. Since the Super Edition is compatible with the analog version, this version is in an awkward position. (Of course it can be used normally)

Super version (not recommended) : Further upgrade version, adding custom parameters and modes. According to the current situation, Microsoft's renewal requirements are very low, and this item is not required for the time being.

The above recommendations/non-recommendations are just personal opinions, please choose the version by yourself, and you can use it at the same time .

step
😊 😊 😊 😊 😊 😊

Please note! Please note! Please note!

***If there are errors/problems, please see : common errors and solutions/update log

*** The original tutorial/blog seems to be broken, watch the video tutorial , too lazy to add, ORZ. (Or go online to search, there are a bunch of reprints, keyword: github action e5 renewal)

*** The azure management page used when registering the app , or directly to the dashboard to find the registration app option

***[Redirect URI] Fill in the content: http://localhost:53682/

*** To download rclone, please Baidu and Google by yourself , the official website seems to be rclone.org

😧 😧 😧 😧 😧 😧

The first step is to browse the original tutorial to learn how to get the application id, secret, and refresh_token to facilitate the next operation.

The second step is to log in/create a new github account, go back to the project page, click on the fork of the project code in the upper right corner to your own account, and then an identical project will appear under your account, and the next operations are in yours Under the project. (If you can't see the picture/picture crack, please go online scientifically)

image

Obtain the application id, secret, and refresh_token according to the original tutorial (copy and save by yourself, pay attention to distinguish the id secret, don’t confuse it)

Then edit 1.txt in your project online, and paste the entire refresh_token into it (there is my data, delete or overwrite it first). (Do not change 1.py)

The location of refresh_token is shown below. Copy the content in the double quotes immediately following refresh_token (framed by the red vertical line), don't copy the double quotes into it. After copying into 1.txt, be careful not to leave spaces or blank lines at the end

image

The third step is to click on the upper column Setting> Secrets> Add a new secret, and create two new secrets as shown in the figure: CONFIG_ID and CONFIG_KEY.

The contents are as follows: (change your application id to your application id, and your application secret to your secret, do not move the single quotes)

CONFIG_ID

= R & lt ID ' your application ID '
CONFIG_KEY

r = Secret ' your application confidential '
image

The final format should look like this:

image

The fourth step, enter your personal settings page (the upper right corner of the picture Settings, not the settings in the warehouse), select Developer settings> Personal access tokens> Generate new token,

image image

Set the name to GITHUB_TOKEN, then check repo, admin:repo_hook, workflow and other options, and finally click Generate token.

image image image

Step 5, click on the star/star in the upper right corner to call it immediately, and then click on the Action above to see the running log of each time and check the running status

(You must click in Test Api to see if the api is called in place and if there is an error. The Auto Api outside can only indicate that the operation is normal. We also need to confirm that the 10 api calls are successful, just like the one in the picture. .If a few apis are missing, either the api permissions are not properly assigned when registering the application; or the onedrive is not logged in to activate onedrive, log in to activate it)

image

The sixth step, if there is no error, it is done! ! Then see if you want to modify the following timing times. If you don't plan to modify it, ignore it.

Then come back the next day to confirm whether it is running automatically (whether there are more in the ation) , if yes, just ignore it, it's over.

I set it to run automatically every 6 hours and call 3 rounds each time (click on the star/star in the upper right corner to call it immediately), you can modify it at your discretion (I don’t know how many calls and how long to keep active):

Timing automatic start to modify the place: (in the .github/workflow/AutoApiSecret.yml file, self-Baidu cron timing task format, the shortest time every 5 minutes)
image

Modify the number of each round: (at the end of 1.py)
image

Digression
Api call You can go to the graph browser to take a look, learn to modify what api to call (the most important thing is to call outlook, onedrive) https://developer.microsoft.com/zh-CN/graph/graph-explorer/ preview

Introduction to GithubAction
Provided virtual environment:

· 2-core CPU · 7 GB RAM memory · 14 GB SSD hard disk space

Use restrictions:

Each warehouse can only support 20 concurrent workflows.
GitHub API can be called 1000 times per hour.
Each job can be executed for up to 6 hours.
Users of the free version support a maximum of 20 concurrent jobs, and macOS only supports a maximum of 5.
The monthly accumulative usage time of the private warehouse is 2000 minutes, after exceeding it is $0.008/min, and the public warehouse is unlimited.
(The public warehouse we use here, logically, you can set up an infinite loop call, and then start it once every 6 hours to ensure 24 hours a day call)

At last
The tutorial is very straightforward, I should be able to do it!

Code noob, forgive me! If you have any questions/recommendations, please click on the issues above to post, or PY to me: wz.lxh@outlook.com

Q group: 657581700 (project related discussions)

Finally, thank you again for shady/paran boss

———— wangziyingwen/kuan id-curly hair fungus
