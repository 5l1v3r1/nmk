# nmk[![Bash4.2-shield]](http://tldp.org/LDP/abs/html/bashver4.html#AEN21220) [![License-shield]](https://raw.githubusercontent.com/v1s1t0r1sh3r3/airgeddon/master/LICENSE.md)   
"Tool kit" to generate the default WPS  PIN from spanish Livebox 2.1 and Livebox Next by Orange.  
[![livebox1]]  

# Description
**N**aranja **M**ekani**K** (**nmk**) is a tool kit that proposes different ways to generate the default WPS PIN from: 
 - Arcadyan ARV7519RW22 
 - Arcadyan ARV7520CW22  
 - Arcadyan VRV9510KWAC23  
The two frist Access Points are also known as **Livebox 2.1** and the third one is known as **Livebox Next**

 
 # About the WPS breach
The PIN algorithm was investigated and found by **wifi-libre** members: [Todo sobre al algoritmo WPS Livebox Arcadyan (Orange-XXXX)](https://www.wifi-libre.com/topic-869-todo-sobre-al-algoritmo-wps-livebox-arcadyan-orange-xxxx.html#p7018)  
It is similar to the one discovered by **Stefan Viehböck** on Arcadyan easy-box: [(Vodafone EasyBox Default WPS PIN Algorithm Weakness](http://seclists.org/fulldisclosure/2013/Aug/51)  
0range has several millions of clients in Spain and has been using exclusivly this three AP models since 2012. 
**Notice that Orange disabled remotely the WPS PIN mode on this devices since the publication of the full disclosure. The vulnerability is no longer exploitable unless the device was not actualized since August-September 2017**


# Dependencies
**nmk.sh** requires **wash 1.6.3** (or a superior version) and its dependencies.  
Steps to follow in a debian based system in order to install **the latest version of reaver** (it includes **wash**):  
 - Install the dependencies    
~~~
sudo apt install libpcap-dev
~~~
 - Install reaver
~~~
git clone https://github.com/t6x/reaver-wps-fork-t6x.git
cd reaver-wps-fork-t6x/src/
./configure
make
sudo make install
~~~  
Visit [reaver t6x repository](https://github.com/t6x/reaver-wps-fork-t6x) for more information about wash and reaver.  


# How to use nmk.sh?
 - Clone this repository  
 ~~~
 git clone https://github.com/kcdtv/nmk.git
 ~~~
 - Execute the script with administrator privileges
 ~~~
 cd nmk; sudo bash nmk.sh
 ~~~  
 
 - If several interfaces are avalaible user is prompted to choose one  
 [![livebox3]]  
 - Once an interface is selected the scan begins and when a vulnerable target is detected it is reported with its PIN genrated  
 [![livebox4]]  
 - Press CTRL + C to stop the scan and the script.  
 Interface is left in monitor mode in order to perform a reaver attack with the default PIN.  
 In good conditions the WPA keys from ARV7520CW22 and VRV9510KWAC23 are recovered inmediatly 
 Due to a very bad implementation of the WPS protocole, recovering the WPA key from the ARV7519RW22 is extremly tedious (to not say impossible).   
   
# How to use orangen.py
```
python orangen.py < 4 last digits mac WAN > < 4 last digits serial > 
```
free tips: The four last digits from WAN mac are the same than the four last digits from default eSSID. If default eSSID is not used you can get the 4 digits by substracting 2 from bSSID (in base 16).  
  
  
# How to use orangen.sh  
Locate your terminal in your "nmk" folder and invocate bash to execute the script  
```
bash orangen.sh
```  
User will be prompted to enter bSSID (from the 2.4Ghz network) and the four last digits from serial number.  


# Credits
Full disclosure "Arcadyan livebox PIN generator" is a colective work  by **wifi-libre**, scripts by **kcdtv**





[livebox1]: https://www.wifi-libre.com/img/members/3/livebox_default_PIN_4.jpg
[lievbox2]: http://pix.toile-libre.org/upload/original/1503195806.png
[livebox3]: http://pix.toile-libre.org/upload/original/1503190103.png
[livebox4]: http://pix.toile-libre.org/upload/original/1503191121.png
[lievbox5]: http://pix.toile-libre.org/upload/original/1503197042.png
[Bash4.2-shield]: https://img.shields.io/badge/bash-4.2%2B-blue.svg?style=flat-square&colorA=273133&colorB=00db00 "Bash 4.2 or later"
[License-shield]: https://img.shields.io/badge/license-GPL%20v3%2B-blue.svg?style=flat-square&colorA=273133&colorB=bd0000 "GPL v3+"  
