# Install an old Samsung Printer on macOS Catalina BigSur, Monterey, Sonoma using outdated Splix 2.0.0

> clp500.ppd   clp610.ppd   ml1610.ppd   ml1710.ppd   ml2010.ppd   ml2251.ppd   ml3050.ppd   scx4500.ppd  clp510.ppd   ml1510.ppd   ml1630.ppd   ml1740.ppd   ml2150.ppd   ml2510.ppd   ml3560.ppd   clp550.ppd   ml1520.ppd   ml1640.ppd   ml1750.ppd   ml2250.ppd   ml2550.ppd   scx4200.ppd 
 

This example is for ML-1510 rename model name to yours

- Download and install Samsung Printer Drivers v3.92
```
https://ftp.hp.com/pub/softlib/software13/printers/SS/Print_Common_SW/Samsung_Mac_10.15_Driver_V3.92.00.dmg
```
- Download splix-2.0.0
```
https://github.com/peekpt/Old-Samsung-Printer-Splix-Catalina/raw/main/Splix-2.0.0.mpkg.zip
```
- Unzip and move Splix-2.0.0.mpkg file to your Desktop

- Open Terminal then copy pstoqpdl and rastertoqpdl files to the library:
```
sudo cp ~/Desktop/Splix-2.0.0.mpkg/Contents/Packages/target.pkg/Contents/usr/libexec/cups/filter/* /Library/Printers/Samsung/UPD/Filters/ 
```
- Copy your respective ppd file to the library renaming it (without extension) to "Samsung ML-1510 Series" (you need to put a "\\" before spaces)
```
sudo cp ~/Desktop/Splix-2.0.0.mpkg/Contents/Packages/target.pkg/Contents/usr/share/cups/model/samsung/ml1510.ppd /Library/Printers/PPDs/Contents/Resources/Samsung\ ML-1510\ Series
```

- Make the file executable:

```
sudo chmod +x /Library/Printers/PPDs/Contents/Resources/Samsung\ ML-1510\ Series
```

- Edit file using nano 
```
sudo nano /Library/Printers/PPDs/Contents/Resources/Samsung\ ML-1510\ Series
```
- Change the line
> *cupsFilter: "application/vnd.cups-raster 0 rastertoqpdl"

 to:
> *cupsFilter: "application/vnd.cups-raster 0 /Library/Printers/Samsung/UPD/Filters/rastertoqpdl"

(ctrl + x to save)...


- Compress gzip the file and make it readable
```
sudo gzip /Library/Printers/PPDs/Contents/Resources/Samsung\ ML-1510\ Series
sudo chmod o+r /Library/Printers/PPDs/Contents/Resources/Samsung\ ML-1510\ Series.gz
```

- Make a folder with the name of your model in the library

```
sudo mkdir /Library/Printers/Samsung/ML-1510
```
- Copy the folder contents from ML-2160 to your folder model

```
sudo cp /Library/Printers/Samsung/ML-2160/* /Library/Printers/Samsung/ML-1510
```
- Change permissions

```
sudo chmod -R o+r /Library/Printers/Samsung/ML-1510
```

- Rename the .icns file
```
sudo mv /Library/Printers/Samsung/ML-1510/ML-2160.icns /Library/Printers/Samsung/ML-1510/ML-1510.icns
```
- Plug in your printer

- Add printer on your system prefs and use driver "Samsung ML-1510, Splix V. 2.0.0"


**Happy printing!**



  
