---
title: "How To Create a Payment Form on WordPress using Flutterwave"
datePublished: Sun Feb 13 2022 19:43:17 GMT+0000 (Coordinated Universal Time)
cuid: ckzlodkv00159rks13hirg0bp
slug: how-to-create-a-payment-form-on-wordpress-using-flutterwave
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1644297911443/H5zi1EK2y.png
tags: wordpress-plugins, wordpress, 2articles1week

---

Making payments online should be seamless and less frustrating. I conquered my fear and tested out Flutterwave and I was really impressed.  Here is how to create a simple payment form using Flutterwave and WordPress.

## What you'll need

- Xampp
- WordPress
- Flutterwave Account (Test Mode/Live)

To get started with WordPress in your local development environment, here is a step by step guide:

[How To Install WordPress in Windows](https://chrisdevcode.hashnode.dev/how-to-install-wordpress-in-windows)

## Creating Flutterwave Account

1. Create a flutterwave account.
2. Go to settings, and under the `API` tab, you'll get your API keys.


![flutterwave_dash.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644776955114/KfEJop0ox.png)

## Flutterwave WordPress Plugin

Flutterwave has a built-in WordPress plugin. 

On your WordPress Admin page, go to `plugins` and click on `add new`.

Search for `Flutterwave Payment Forms`


![Screenshot_1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644777426214/lVLMhLTES.png)

Install the plugin by Flutterwave Developers, (top left on the screenshot). After installation is complete, click on `Activate` to activate the plugin.


![Screenshot_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644778135462/LPI6T_0r_.png)

After activation, you'll be taken to the installed plugins page, and on the top of the page, click on the big blue button to enter your Flutterwave API keys.


![Screenshot_3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644778311899/K2O6i6M-a.png)

Select the payment method from the dropdown options:

![Screenshot_4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644778902961/JUqHF297v.png)

Scroll down to select payment currency

![Screenshot_5.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644778971053/hREgPaa4u.png)

Other fields are optional, go ahead and save the settings.

## Using flutterwave shortcode

To be able to add the flutterwave payment forms, simply add the shortcodes into a WordPress page. The codes are as follows:

```shell
// button
 [flw-pay-button]

// button with text
[flw-pay-button]Button Text[/flw-pay-button]
```

On the editing page, select `shortcode` from the editing block:


![Screenshot_6.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644780639270/ei9otEKrt.png)

Insert the shortcode of your choice (flutterwave shortcode):

![Screenshot_7.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644780711065/mf3CrDmY_.png)

Save and preview the page:


![Screenshot_8.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644780754845/XV_eLVtiV.png)

## Testing the Payment Form

Fill out the form and click on `Pay Now` to see what happens:


![Screenshot_9.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644781128278/fo3N_aeDg.png)

You'll be redirected to a flutterwave modal box:


![Screenshot_10.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644781171454/JBpYRnmfA.png)

As shown, a user can select a preferred payment method

Once the payment is complete, the transaction will reflect on your flutterwave dashboard, under the `transactions` tab:


![Screenshot_13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644781272833/PzOB6rTh6.png)

### Parting Short

Flutterwave has made it simpler and easier to add payments functionalities, WordPress is one of the examples. It also gives you an option for mobile payments (M-Pesa for my Country) and card payments