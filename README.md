========================================================================================
Ionic Capacitor Sunmi T2 Inner Printer App
========================================================================================
README

By:
Nathaniel Tiempo
Kyla Yvonne Belmonte
Mary Grace Versoza

Plugin based on: https://github.com/labibramadhan/cordova-sunmi-inner-printer

=========================================================================================

Download, extract, and install the zip file *cordova-plugin-sunmi-inner-printer* using npm

Note: This is a cordova plugin thus, you will use npm to install this on a capacitor project

command: npm install filepath
example: npm install C:\Users\nathaniel\Desktop\printer\cordova-plugin-sunmi-inner-printer

After installing, sync your added plugin to the capacitor project using this command:
> npx cap sync

To check whether the plugin is installed, you use the command:
> npx cap ls

To use the inner printer, you need to add this to your .TS file above @Component:

/*
declare var sunmiInnerPrinter: any;
*/

Then add these code below for paper cutting.

/*

BufferToBase64(buf) {
  var binstr = Array.prototype.map.call(buf, function (ch) {
    return String.fromCharCode(ch);
  }).join('');
  return btoa(binstr);
}

*/

You can now print using the SUNMI Inner Printer. 
Just use these sample code under print function below:

/*
  print() {
	/*These codes are used for cutting the paper*/
    var cutpaper = [0x1d, 0x56, 0x42, 0x00];
    var cutpaperUint8 = new Uint8Array(cutpaper);
    var cutpaperBase64 = this.BufferToBase64(cutpaperUint8);
	/*----------------------------------------*/
    sunmiInnerPrinter.printerInit();
    sunmiInnerPrinter.printString("\nYoshii 2022 - kjadbhjkabfjkagbef");
    sunmiInnerPrinter.printQRCode("Kyla", 10, 30);
    sunmiInnerPrinter.printString("\n");
    sunmiInnerPrinter.sendRAWData(cutpaperBase64); //Paper cut function
  }

*/

Note: Keep in mind to always put "\n" when printing a string in order for the inner printer to print the string.


Thank you! Happy Coding!
