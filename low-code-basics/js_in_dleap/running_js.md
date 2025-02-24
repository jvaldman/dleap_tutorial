# Running JavaScript in HCL Domino Leap

Most objects in Domino Leap have various events asosieated with them. Most often events are used within item scope but there are events also on pages, forms and the application. Item are easily accesible in Editor.

todo přidat side panel

TODO obrázek eventů - přehledová stránka všech

## JavaScript Triggered In Events

In HCL Domino Leap you can create custom code that is triggered by user interactions or other events in the
application. 


::: details Create an Event - Step-by-Step Guide

1\. Start by navigating to design page.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/88271664-717d-4069-a5e1-393fc55281b8/ascreenshot.jpeg?tl_px=0,0&br_px=1934,1081&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=-9,48)

2\. Click item you want to edit.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/7a9ad6ee-9666-4cd4-93e0-0c5291cbaeab/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=1934,1081&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=513,142)

3\. In item side panel switch to "Events" tab.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/b1826d93-cb8f-4179-ad5d-debd14005564/ascreenshot.jpeg?tl_px=1906,0&br_px=3841,1081&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=828,118)

4\. Click the event you want to add or change.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/e205881f-8dab-49df-bbe8-428a617d85df/ascreenshot.jpeg?tl_px=1906,14&br_px=3841,1095&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=744,277)

5\. You can write your custom JavaScript into "Custom Actions" section.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/07c34407-4666-464d-9aeb-046727d9d94c/ascreenshot.jpeg?tl_px=436,242&br_px=2371,1323&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,277)

6\. To select an item element to add it into your code press `CTRL` + `Space`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/fc0de4f8-bc97-4c33-9226-989d29d62359/ascreenshot.jpeg?tl_px=985,788&br_px=2920,1870&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,352)

7\. If you press `CTRL` + `Space` once more you can add code segments into your code.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/c972fdc6-5e51-4606-88e7-5b601cdd0a6e/ascreenshot.jpeg?tl_px=802,239&br_px=2737,1320&force_format=png&width=1120.0&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=524,277)

8\. As you can see, for each code segment has been added.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2024-04-02/de437f04-614e-4ad7-bceb-97180215497e/user_cropped_screenshot.jpeg?tl_px=953,394&br_px=2888,1475&force_format=png&width=1120.0)

:::

todo - do sth when item value is modified - on item change
todo - do sth when page is shown 
todo - do sth on app start - initialize constanty v globálních datech


## Asynchronous Operations

Because HCL Domino Leap is built using JavaScript, which is asynchronous by nature, you need to understand how to
synchronize your calls to ensure that your application behaves as expected.

### Service Call + Custom JavaScript

When using service call from UI (1) and custom JavaScript (2), there is no way you can synchronize these two operations.
Here is an example to give you a better picture:

![](./async_image2.png)

The solution to this problem is to write everything as custom JavaScript and use the service call from there. You can
find more information on synchronization using `onCallFinished` event in
the [Service Calls](/low-code-basics/js_in_dleap/services_js.html#synchronizing-service-calls) page.

## Events Cascading Issue

When you want to update multiple values after change such as service call in sequence, then it is a case of cascading
events illustrated in the following example:
![](./async_valu_update.png)
To solve this issue, you can use the `onCallFinished` event described in
the [Service Calls](/low-code-basics/js_in_dleap/services_js.html#synchronizing-service-calls) page. 
