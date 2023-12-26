# setup-jupyterlab

from https://docs.vultr.com/how-to-set-up-a-jupyterlab-environment-on-ubuntu-22-04

<h3>Install the Required Packages</h3>

sudo pip install -U jupyterlab

<h3>Configure the JupyterLab Server</h3>
python3 -c "from jupyter_server.auth import passwd; print(passwd('YOUR_PASSWORD'))"
jupyter lab --generate-config
nano ~/.jupyter/jupyter_lab_config.py

c.ServerApp.password = 'PASSWORD_HASH'
c.ServerApp.allow_remote_access = True

sudo ufw disable

jupyter lab --ip 0.0.0.0

<h3>Daemonize the JupyterLab Server</h3>

sudo nano /lib/systemd/system/jupyterlab.service

[Unit]
Description=JupyterLab Server

[Service]
User=USER
Group=USER
WorkingDirectory=/home/USER/jupyterlab
Environment="PATH=VIRTUAL_ENV_PATH_HERE"
ExecStart=/usr/local/bin/jupyter-lab --config=/home/USER/.jupyter/jupyter_lab_config.py

[Install]
WantedBy=multi-user.target

mkdir ~/jupyterlab
sudo systemctl daemon-reload
sudo systemctl start jupyterlab
sudo systemctl status jupyterlab
