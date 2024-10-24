# Launch Jupyter on server

**1. Log in to server**

`ssh username@server_ip` \
`ssh Marina.Pak@10.30.194.110`

**2. Run Jupyter**

```bash
export PATH=/opt/anaconda3/bin/:$PATH # export path not to write full path to jupyter
jupyter lab --no-browser
```

Since there is no browser on server we set `--no-browser`. Jupyter will be launched in a free port. In my case it's 8891: 

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/port.png' width='700px'>

**3. Redirect the port to your browser**

Open the terminal/command line on your computer **(not server!)** and run the following command:

```bash
ssh -L localhost:port-for-your-browser:localhost:port-on-server username@10.30.194.110
```

`-L` stands for local. If you don't have any opened session of Jupyter, you may use port 8888 for convenience. If it is occupied, use any other YYYY. To check if the port on your local machine is free,  run `localhost:YYYY` in browser. If it says "This site can’t be reached", the port is free.

Example:

```bash
ssh -L localhost:8888:localhost:8891 Marina.Pak@10.30.194.110
```

If you are asked "Are you sure you want to continue connecting (yes/no)?" type yes and press Enter. Then enter your server password.

**4. Open localhost:YYYY in your browser**

Open localhost:YYYY in your browser (In my case it's localhost:8888). You will be asked for a token. Copy the token from terminal and paste into the browser field. Jupyter Notebook on server will be launched in your browser.

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/paste_token.png' width='500px'>
<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/token.png' width='700px'>

Now we can work on server in Jupyter!

**Important:** don't close the terminal window on your local machine where you launched the command from Section 3. If you close it, the conection with server will be lost.

Nice thing about Jupyter lab is that you can Download and Upload the files from and to server through the GUI in the browser:

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/upload_download.png' width='500px'>

<hr>

To see the list of your launched notebooks, run `jupyter notebook list`.

To shut the notebook use Ctrl + C or the command `jupyter notebook stop <port number>`

You may launch Jupyter in the screen to be able to leave the session in the termial and still use Jupyter from server in your browser. `-S` flag sets the name of your screen.

```bash
screen -S jp
```

To leave the screen and get back to the main session press `Ctrl + A` and then `D`. To see the list of your screens use `screen -ls`. To enter the screen type `screen -r jp`.
