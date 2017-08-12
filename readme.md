pour installer autocad sur linux (ubuntu 16.04)

source : 

https://appdb.winehq.org/objectManager.php?sClass=version&iId=9306

installer wine-2.0.2 (ajouter le repository)

```
wget https://dl.winehq.org/wine-builds/Release.key
sudo apt-key add Release.key
sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'

```
desinstaller vieux wine si present

```
sudo apt-get remove wine
```
enlever le dossier de wine pour etre sur que wine et ses composantes sont en 32bit
```
rm -rf ~/.wine
```

installer wine stable

```
sudo apt-get install winehq-stable
```

exporter la variable WINEARCH dans ~/.bashrc pour rouler wine en 32 bit
```
echo "export WINEARCH=win32" >> ~/.bashrc 
```

rouler winetricks et ajouter  (commande a tester)
```
winetricks dotnet11 dotnet11sp1 dotnet20 
comdlg32ocx vb6run (installe automatique?)
```

rouler l'installation de autocad 32 bits via la commande pour avoir le debug
```
wine [dossier ou est autocad]/x86/setup.exe
```
dans mon cas deux fichiers etaient manquant de mon iso soit :

```
ISYS.CFG
ISYS.FLD
```
donc faire une copie si necessaire de par example ISYS.CAT vers les fichier 
(probablement que c'est pas bon de faire ca...)

Une fois l'installation effectuee avec succes avant de lancer autocad, executer
```
./first-run
```
cela va faire un backup du system de wine afin de pouvoir reseter le trial

si le logiciel ce plait que ca fait plus de trente jour, rouler
```
reset-trial
```

enjoy

