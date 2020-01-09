
## 2020 Danimae Vossen
## Uncomment the boxes you want to run, then run 'vagrant up' from the command line to lauch them simultaneously
## If you need to run multiples independently, copy this file into another directory and select individual boxes

## Recommended choices denoted by *

## Prerequsite (Optional) vagrant plugin install vagrant-disksize
## Prerequsite (Optional) vagrant plugin install vagrant-vbguest

boxes = [

  ##### LINUX VM #####

  # "f500/ubuntu-lucid64",                             # Ubuntu 10.04
  # "3dox/ubuntu-oneiric",                             # Ubuntu 11.04
  # "hashicorp/precise64",                             # Ubuntu 12.04
  # "rafaelrosafu/raring64-vanilla",                   # Ubuntu 13.04
  # "ubuntu/trusty64",                                 # Ubuntu 14.04
  # "bento/ubuntu-14.04",                              # Ubuntu 14.04
  # "wzurowski/vivid64",                               # Ubuntu 15.04
  # "geerlingguy/ubuntu1604",                          # Ubuntu 16.04 *
  # "mrlesmithjr/zesty64",                             # Ubuntu 17.04
  # "ubuntu/bionic64",                                 # Ubuntu 18.04 *
  # "socialwifi/ubuntu-gui",                           # Ubuntu 18.04 *
  
  # "danimaetrix/openSUSE-Leap-42.3",                  # OpenSUSE *     
  # "opensuse/openSUSE-42.2-x86_64",                   # OpenSUSE
  # "webhippie/opensuse-13.2",                         # OpenSUSE
  # "bento/opensuse-leap-42.1",                        # OpenSUSE
  
  # "generic/rhel7",                                   # Redhat *
  # "thinktainer/centos-6_6-x64",                      # Centos 6 *
  # "ddacunha/CentOS-7.2",                             # Centos 7
  # "generic/fedora27",                                # Fedora *
  # "generic/gentoo",                                  # Fedora *

  # "wvera/sles12sp1",                                 # SLES 12 / SP 1
  # "trueability/sles-12-sp1",                         # SLES 12 / SP 1
  # "danimaetrix/sles12-sp1-sdk",                      # SLES 12 / SP 1 + SDK *

  # "debian/wheezy64",                                 # Debian
  # "debian/contrib-jessie64",                         # Debian
  # "generic/debian9",                                 # Debian *

  ##### MACOS VM #####

  # "danimaetrix/macOS-high-sierra",				   # MacOSX High Sierra
  # "danimaetrix/macOS-mojave",						   # MacOSX Mojave

  ##### WINDOWS VM #####

  # "danimaetrix/windows-95",						   # Windows 95
  # "danimaetrix/windows-vista-sp2",				   # Windows Vista
  # "danimaetrix/windows-7-ultimate",				   # Windows 7 Ultimate
  # "danimaetrix/windows-8.1",						   # Windows 8.1
  # "danimaetrix/windows-server-2012R2",			   # Windows Server 2012 R2
  # "danimaetrix/windows-server-2012R2-core",		   # Windows Server 2012 R2 (Core)
  # "danimaetrix/windows-10-professional",			   # Windows 10 Professional
  # "danimaetrix/windows-server-2016-datacenter"	   # Windows Server 2016 Datacenter

]

Vagrant.configure("2") do |config|  
	boxes.each do |key|
		boxName = key.sub("/","-")
		vbox = boxName

		puts "\e[32m\nBox details\n\e[0m-------------"
		puts "name: " + "\e[36m" + boxName + "\e[0m" 
		puts "ssh:  \e[36mvagrant ssh " + boxName + "\e[0m "
		puts 

		config.vm.network :public_network   
		config.disksize.size = '80GB'

		config.vm.define vbox do |vbox| 

			#vbox.vm.synced_folder ".", "/vagrant", disabled: true
			#vbox.vm.synced_folder "D:\\PiBackup", "/pi"

			vbox.vm.box = key
			vbox.vm.boot_timeout = 600
			vbox.ssh.insert_key = false
			vbox.vbguest.auto_update = false      
			vbox.vm.provider "virtualbox" do |v|
				v.customize ["modifyvm", :id, "--memory", 4048]
				v.customize ["modifyvm", :id, "--cpus", 2]
				v.customize ["modifyvm", :id, "--vram", 256]
				v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
				v.gui = false		
				v.name = boxName
			end
		end
	end
end