# Jupyter Notebook

Jupyter Notebook으로 GUI SSH 구현하기.

1. sudo apt-get update
2. sudo apt-get install python3-pip
3. sudo pip3 install notebook
4. python3
5. from notebook.auth import passwd
6. passwd()
7. SET PASSWORD
8. Copy sha1
9. exit()
10. jupyter notebook --generate-config
11. vi (open jupyter_notebook_config.py)
12. c = get_config()
13. c.NotebookApp.password = 'hash'
14. c.NotebookAPp.ip = 'server ip'
15. c.NotebookApp.notebook_dir = '/'
16. sudo jupyter-notebook --allow-root
17. check website login
18. Ctrl + Z (Stop jupyter notebook)
19. bg
20. disown -h
21. sudo netstat -nap | grep 8888
22. sudo kill -9 (jupyter process number)
23. cd /home/ubuntu
24. mkdir ssl
25. cd ssl
26. sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch
27. open jupyter nodebbok config
28. c.NotebookApp.certfile = u'/home/ubuntu/cert.pem'
29. c.NotebookApp.keyfile = u'/home/ubuntu/cert.key'
30. save
31. sudo jupyter-notebook --allow-root
32. Ctrl + C -> y 
33. which jupyter-notebook
34. sudo vi /etc/systemd/system/jupyter.service

[Unit]

Description=Jupyter Notebook Server

[Service]

Type=simple

User=ubuntu

ExecStart=/usr/bin/sudo /usr/local/bin/jupyter-notebook 
--allow-root --config=/home/ubuntu/.jupyter/jupyter_notebook_config.py

[Install]

WantedBy=multi-user.target

36. sudo systemctl daemon-reload
37. sudo systemctl enable jupyter
38. sudo systemctl start jupyter
39. sudo systemctl status jupyter