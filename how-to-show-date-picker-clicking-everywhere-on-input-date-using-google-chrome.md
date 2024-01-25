On Chrome, by default, the user can only trigger date picker from input type of date when he hits the calendar icon. Here is a demo of what happens when the user tries to click on input besides the icon:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671662529577/-KYWEvvTX.gif align="center")

This can be awful for the user, but there is a good solution that uses only CSS. The calendar can be accessible with the pseudo-class `-webkit-calendar-picker-indicator`, the icon is responsible for triggering the date picker, so it is possible to make the trigger occupy the whole input with this code below:

```css
input[type="date"] {
    position: relative;
}

input[type="date"]::-webkit-calendar-picker-indicator {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: auto;
    height: auto;
    color: transparent;
    background: transparent; */you need to disable the background becasue the icon can repeat based on input size */
}
```

How the input will work after applying the code above:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1671664313610/sBTChMvJI.gif align="center")

You also can change the value from **width** and **height** to 100%, but you have to be careful with your **box-sizing** props and the **borders** from the input. [Here is](https://www.quora.com/What-does-width-100-do-in-CSS) a recommendation if you want to understand more about how the CSS handles percentage values.
