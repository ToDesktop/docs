# 🖨 Printing

Some applications e.g. event check-in may want to programatically print without going through the browser dialog.

We expose two methods to your app's window: `window.todesktop.contents.getPrinters()` to get the device's saved printers and `window.todesktop.contents.print()`  to do the actual printing.

If you have used Electron before, these methods will look familiar as we use the same function signatures.

## Print the current page

`window.todesktop.contents.print([options], [callback])`

```javascript
window.todesktop.contents.print(
  {
    /*
      Skips the browser print dialog and begins printing.
      Boolean. Optional. Defaults to false.
    */
    silent: true,
    /*
      Print the background color and image of the page.
      Boolean. Optional. Defaults to false.
    */
    printBackground: false,
    /*
      Set the printer to use. You can get the available
      printer names with window.todesktop.contents.getPrinters()
      String. Optional. Defaults to ''.
    */
    deviceName: 'EPSON_WF_7610_Series'
  },
  /*
    success will be a boolean indicating whether or not
    the printing call was successful.
  */
  success =>
    success
      ? console.log('Printed successfully.')
      : console.error('Could not print the page.')
);
```

## Get available printers

`window.todesktop.contents.getPrinters()` will return an array of available printers.

```javascript
const printers = window.todesktop.contents.getPrinters();

console.log(printers[0]);
// {
//  name: 'Zebra_LP2844',
//  description: 'Zebra LP2844',
//  status: 3,
//  isDefault: false,
//  options: {
//    /* ... */
//  }
//}
```



