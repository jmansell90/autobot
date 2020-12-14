###Installation Instructions
After installing requirements with pip, just run ./install which will copy all files and create the systemd service
~~~
pip3 install -r requirements
./install
systemctl enable --now autobot
~~~

###To run locally:
Install Requirements with pip:
~~~
pip3 install -r requirements
~~~
copy autobot.yml from ./lib and edit to suit.
~~~
cp lib/autobot.yml autobot.yml
vi autobot.yml
~~~
Then run ./autobot to manage media.
~~~
./autobot
