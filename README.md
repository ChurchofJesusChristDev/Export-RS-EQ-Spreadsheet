# Export-RS-EQ-Spreadsheet

Export the EQ / RS list LCR to a Spreadsheet (Google Sheets, Microsoft Excel, CSV, TSV)

Very easy to do:

1. Sign in at <https://lcr.churchofjesuschrist.org/>
2. Visit the EQ or RS member page
   - The URL looks like this: <https://lcr.churchofjesuschrist.org/orgs/100001?lang=eng&members>
3. <kbd>Cmd ⌘</kbd> + <kbd>Alt ⌥</kbd> + <kbd>i</kbd> to open the JavaScript ***I***nspector in Chrome (or Brave)
   - or Menu => More Tools => Developer Tools (or JavaScript Console / Inspector)
   - or Ctrl + Shift + I (on Windows)
4. Copy and Paste this into the console
   ```js
   var members = $$('.members tr').map(function ($tr) {
     var $$td = $tr.querySelectorAll('td');
     if (!$$td.length) { $$td = $tr.querySelectorAll('th'); }
     return Array.prototype.slice.apply($$td).map(function ($td) {
       return '"' + $td.innerText/*.replace(/\n/g, ' ')*/.replace(/"/g, '""') + '"';
     }).slice(2).join('\t');
   }).join('\n');
   console.log(members);
   ```
5. Then copy and paste that list into a spreadsheet.

Don't mind that it looks weird when you copy it, It'll paste perfectly.
