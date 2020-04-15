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
  
  apt-get install rofi -y
  
  apt-get install feh -y

##################Editar fichero bspwmrc  

  nano bspwmrc
  
  wmname LG3D &
  
  bspc config pointer_modifier mod1


################guardar fichero bspwmrc

   mkdir scripts && cd scripts && touch bspwn_resize && chmod +x bspwn_resize

   nano bspwn_resize
   
########## Editar fichero bspwn_resize

#!/usr/bin/env dash

if bspc query -N -n focused.floating > /dev/null; then
        step=20
else
        step=100
fi

case "$1" in
        west) dir=right; falldir=left; x="-$step"; y=0;;
        east) dir=right; falldir=left; x="$step"; y=0;;
        north) dir=top; falldir=botton; x=0; y="-$step";;
        south)dir=top; falldir=botton; x=0; y="$step";;
esac

bspc mode -z "$dir" "$x" "$y" || bspc node -z "$falldir" "$x" "$y"


################guardar fichero bspwn_resize
   
   cd ~/.config/sxhkd/

   nano sxhkdrc
   
########## Editar fichero sxhkdrc

#
# wm independent hotkeys
#

# terminal emulator
super + Return
	gnome-terminal

# program launcher
super + d
	rofi -show run

# make sxhkd reload its configuration files:
super + Escape
	pkill -USR1 -x sxhkd

#
# bspwm hotkeys
#

# quit/restart bspwm
super + alt + {q,r}
	bspc {quit,wm -r}

# close and kill
super + {_,shift + }w
	bspc node -{c,k}

# alternate between the tiled and monocle layout
super + m
	bspc desktop -l next

# send the newest marked node to the newest preselected node
super + y
	bspc node newest.marked.local -n newest.!automatic.local

# swap the current node and the biggest node
super + g
	bspc node -s biggest

#
# state/flags
#

# set the window state
super + {t,shift + t,s,f}
	bspc node -t {tiled,pseudo_tiled,floating,fullscreen}

# set the node flags
super + ctrl + {m,x,y,z}
	bspc node -g {marked,locked,sticky,private}

#
# focus/swap
#

# focus the node in the given direction
super + {_,shift + }{Left,Down,Up,Right}
	bspc node -{f,s} {west,south,north,east}

# focus the node for the given path jump
super + {p,b,comma,period}
	bspc node -f @{parent,brother,first,second}

# focus the next/previous node in the current desktop
super + {_,shift + }c
	bspc node -f {next,prev}.local

# focus the next/previous desktop in the current monitor
super + bracket{left,right}
	bspc desktop -f {prev,next}.local

# focus the last node/desktop
super + {grave,Tab}
	bspc {node,desktop} -f last

# focus the older or newer node in the focus history
super + {o,i}
	bspc wm -h off; \
	bspc node {older,newer} -f; \
	bspc wm -h on

# focus or send to the given desktop
super + {_,shift + }{1-9,0}
	bspc {desktop -f,node -d} '^{1-9,10}'

#
# preselect
#

# preselect the direction
super + ctrl + alt + {Left,Down,Up,Right}
	bspc node -p {west,south,north,east}

# preselect the ratio
super + ctrl + {1-9}
	bspc node -o 0.{1-9}

# cancel the preselection for the focused node
super + ctrl + space
	bspc node -p cancel

# cancel the preselection for the focused desktop
super + ctrl + shift + space
	bspc query -N -d | xargs -I id -n 1 bspc node id -p cancel

#
# move/resize
#

# expand a window by moving one of its side outward
#super + alt + {h,j,k,l}
#	bspc node -z {left -20 0,bottom 0 20,top 0 -20,right 20 0}

# contract a window by moving one of its side inward
#super + alt + shift + {h,j,k,l}
#	bspc node -z {right -20 0,top 0 20,bottom 0 -20,left 20 0}

# move a floating window
super + ctrl + {Left,Down,Up,Right}
	bspc node -v {-20 0,0 20,0 -20,20 0}
   
#----------------------------------------------------------
# CUSTOM
#----------------------------------------------------------

#Custom move/resize
alt + ctrl + {Left,Down,Up,Right}
        /root/.config/bspwm/scripts/bspwn_resize{west,south,north,east}

# Firefox

super + shift + f
        firefox


23:20


 
