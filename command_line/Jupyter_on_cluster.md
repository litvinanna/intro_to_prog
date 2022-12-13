# Launch Jupyter on cluster

**1. Log in to cluster.**

`ssh username@cluster_ip` \
`ssh Marina.Pak@10.30.194.110`

**2. Run Jupyter.**

```bash
jupyter lab --no-browser
```

Since there is no browser on cluster we set `--no-browser`. Jupyter will be launched in a free port. In my case its 8891: 

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/port.png'>

**3. Redirect the port to your browser.**

Open the terminal/command line on your computer (not cluster!) and run the following command:

```bash
ssh -L localhost:[port for your browser]:localhost:[port on cluster] username@10.30.194.110
```

`-L` stands for local. If you don't have any opened session of Jupyter, you may use port 8888 for convenience. If it is occupied, use any other YYYY. To check if the port on your local machine is free,  run `localhost:YYYY` in browser. If it says "This site can’t be reached", the port is free.

Example:

```bash
ssh -L localhost:8888:localhost:8891 Marina.Pak@10.30.194.110
```

If you are asked "Are you sure you want to continue connecting (yes/no)?" type yes and press Enter. Then enter your cluster password.

**4. Open localhost:YYYY in your browser.**

You will be asked for a token. Copy the token from terminal and paste into the browser field. Jupyter Notebook on cluster will be launched in your browser.

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/paste_token.png' align='center'>
<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/token.png'>

Nice thing about Jupyter lab is that you can Download and Upload the files from anf to cluster through the GUI in the browser:

<img src='https://github.com/litvinanna/intro_to_prog/raw/main/command_line/upload_download.png'>

<hr>

To see the list of your launched notebooks, run `jupyter notebook list`.

To shut the notebook use Ctrl + C or the command `jupyter notebook stop <port number>`

<hr>

You may launch Jupyter in the screen to be able to leave the session in the termial and still use Jupyter from cluster in your browser. `-S` flag sets the name of your screen.

```bash
screen -S jp
```

To leave the screen and get back to the main session press `Ctrl + A` and then `D`. To see the list of your screens use `screen -ls`. To enter the screen type `screen -r jp`.
