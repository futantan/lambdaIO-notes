# parseInt

The safest thing to do is to **always** specify the radix. If you omit the radix, your code will probably still work in 99 percent of cases \(because most often you parse decimals\), but every once in a while it might cause you a bit of hair loss while debugging some edge cases. For example, imagine you have a form field that accepts calendar days or month

如果不指定第二个参数，解析八进制数的时候，会有问题

