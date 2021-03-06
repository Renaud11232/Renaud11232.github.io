# Esher

### [-$ cd ..](../)

Author: [alect096](https://alect096.github.io/CTFs/CSCBE2019/pre-finals_friday/friday_morning/esher/)

For this challenge, we received the following image:

![esher image](./assets/esher_intro.png)

The trick in this case was to use a [website](http://magiceye.ecksdee.co.uk) to be able to see the text hidden in the 3D image.
After to upload the image to the website we need to proceed a 90° rotation to the left.

![result esher](./assets/result.png)

We extract this URL: [bit.ly/2TuD8Zp](http://bit.ly/2TuD8Zp).

This page redirected us to the following address [https://cybersecuritychallenge.be/prefinals/1dedf46e93ff4de7bf254e30d38fbebd2e25d2eb6038bb78df81ac9274b69afd.txt](https://cybersecuritychallenge.be/prefinals/1dedf46e93ff4de7bf254e30d38fbebd2e25d2eb6038bb78df81ac9274b69afd.txt).

We could also download the [file](1dedf46e93ff4de7bf254e30d38fbebd2e25d2eb6038bb78df81ac9274b69afd.txt) and the flag was in the file: `CSCBE{BetterStereoscopyThanColonoscopy}`.
