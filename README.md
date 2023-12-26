# setup-jupyterlab

<ul>
  <li>sudo apt install python3-pip -y</li>
  <li>pip install jupyter</li>
  <li>jupyter notebook --allow-root</li>
  <li>jupyter notebook --generate-config</li>
  <li>jupyter notebook password</li>

edit jupyter_notebook_config.py
c.ServerApp.ip = '0.0.0.0'
c.ServerApp.allow_origin = '*'
</ul>
