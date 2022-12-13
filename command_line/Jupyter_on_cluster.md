**1. Log in to cluster.**

`ssh username@cluster_ip` \
`ssh m.pak@10.30.194.138`

**2. Run Jupyter.**

`jupyter notebook --no-browser --port=9999`

Since there is no browser on cluster we set `--no-browser`. In the `--port` you may specify any number XXXX. By default it is 8888 (when you launch Jupyter on your computer, it starts in the browser window with the adress localhost:8888). If the port is occupied (someone else launched his Jupyter in this port) you will be assigned another port: 

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/1.png'>

**3. Redirect the port to your browser.**

Open the terminal/command line on your computer (not cluster!) and run the following command:

`ssh -L localhost:[port for your browser]:localhost:[port you requested on cluster] username@10.30.194.138`

`-L` stands for local. If you don't have any opened session of Jupyter, you may use port 8888 for convenience. If it is occupied, use any other YYYY. 

Example:

`ssh -L localhost:8888:localhost:9999 m.pak@10.30.194.138`

If you are asked "Are you sure you want to continue connecting (yes/no)?" type yes and press Enter. Then enter your cluster password.

**4. Open localhost:YYYY in your browser.**

You will be asked for a token. Copy the token from terminal and paste into the browser field. Jupyter Notebook on cluster will be launched in your browser.

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/3.png' width='400px'>
<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/4.png'>

<hr>

To see the list of launched notebooks:

`jupyter notebook list`

To shut the notebook use Ctrl + C or the command `jupyter notebook stop <port number>`

<hr>

You may launch Jupyter in the screen to be able to leave the session in the termial and still use Jupyter from cluster in your browser. `-S` flag sets the name of your screen.

`screen -S jp`

To leave the screen and get back to the main session press `Ctrl + A` and the `D`. To see the list of your screens use `screen -ls`. To enter the screen type `screen -r jp`.
