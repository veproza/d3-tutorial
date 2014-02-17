Set correct values in the first column, the rank

We're finally getting down to business. First, we select all the valid rows, after we have created missing rows and removed the redundant ones. So these are actual rows in the document, not "ghost" ones we get via applying data and enter() or exit().

We do the actual filling on the next line. Here, we select the first cell on every line (with td:first-child selector; the "on every line" part is handled for us by D3) and alter its HTML property (the raw content of the <td> node).

We handle all properties (HTML, style, attributes etc.) with **callbacks**. Each callback receives at least two arguments, the **datum** (one element of the *data* array, in our case the *country* object with name and medals properties) and **index**, an integer counter, starting from zero.

We will usually be using the datum argument, as we mostly need the properties of the object; this is one of theh relatively few examples when index is actually useful.

Callbacks can also have more than two arguments. If you use nested data (as we will shortly, when we need to display the medal count dataline for each Country row), you will get an index of the parent data. As an example, when you display fourth medal datapoint of the second country (CZE), you will get a callback with arguments 6, 3, 1 (medalCount, index, parentIndex; indices are zero-based)

Set correct values in the second column, the name

This is an easy one. We select the second cell of every row and again, alter its HTML property. Here we need only the name property of the datum (*country*) argument. Don't forget the return statement, otherwise the cell will be left blank!

Set the third column, the medal count

Now we fill in the sum of the medals array. This demonstrates that the callbacks don't have to be simple one-liners, you can compute anything you want within them. Here, we compute the sum of the medals simply by iterating over each element of the array in the *for loop* and adding it to the *sum* variable. Final line is, as always, returning the desired content.