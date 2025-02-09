# RepairLSI9305-16E
Repair LSI 9305-16e that is reporting Temp/Overheat error with blinking red LED and not detecting arrays

I have seen quite a few of these being sold places like Ebay and Amazon that are reported as good or even new. 

Symptoms: 
-When you connect the card you see a blinking green LED and then when the card reset is done it goes to a solid red LED
-In linux the card will show up in LSPCI BUT if you look at the logs the driver will continuously report overheating errors
-Card will NOT detect any arrays/disks attached. 

In my experience so far none of the cards that I've seen in person showing this error pattern have actually been overheating 
but rather this has been an error state left over from their previous use. 

In order to fix I've had to 
1. Erase the flash
2. write a new firmware image to the card
3. (optionally if you will be using more than one sas card rewrite the sas id to the card)

Almost magically it just works after that in 99% of cards that I've touched. 

For some reason I've had limited luck using the host based sas3flash tool on linux, freebsd or even dos to get this to a consistent 
I've had to use the sas3flash.efi version of the utility. 

In order to fix it I've had to 

1. Download the firmware and sas3flash and efi shell
2. make a fat32 formatted usb drive
3. put the efi shell into the required directory structure and file name required by your motherboard vendor (in my case that is /efi/boot/shellx64.efi
5. boot into the the efi shell (choose the device from your motherboard boot utility)

Most recent firmware download from broadcom https://docs.broadcom.com/docs/9305_16e_Pkg_P16.12_IT_FW_BIOS_for_MSDOS_Windows.zip
Sas3flash tool from broadcom https://docs.broadcom.com/docs/SAS3FLASH_P15.zip 


