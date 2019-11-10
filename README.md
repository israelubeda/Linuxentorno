# Linuxentorno
configurar un buen entorno de trabajo en Linux


   apt-get install bspwm -y
   
   sudo apt-get install libxcb-xinerama0-dev libxcb-icccm4-dev libxcb-randr0-dev libxcb-util0-dev libxcb-ewmh-dev libxcb-keysyms1-dev libxcb-shape0-dev
   
   git clone https://github.com/baskerville/bspwm.git
   
   git clone https://github.com/baskerville/sxhkd.git
   
   $ cd bspwm && make && sudo make install
   
   $ cd ../sxhkd && make && sudo make install
   
   $ mkdir -p ~/.config/{bspwm,sxhkd}
   
   $ cp /usr/local/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm/
   
   $ cp /usr/local/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd/
   
   $ chmod u+x ~/.config/bspwm/bspwmrc
   
   cd ~/.config/bspwm/
   
   nano ~/.xinitrc
   
#Editar fichero  ~/.xinitrc
 
   sxhkd &
   
   exec bspwm
   
#guardar fichero

  apt-get install compton -y

#Editar fichero bspwmrc  

  nano bspwmrc
  
  wmname LG3D &

#guardar fichero

   apt-get install feh -y


 
