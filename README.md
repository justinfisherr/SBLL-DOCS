# Space Beach Law Lab Web Documentation

## Before we start

This document will serve as a guide on how to use/edit the [Space Beach Law Lab website](https://www.spacelawlab.com/) in future iterations of SBLL for developers or non-developers alike. This website follows the 2023 design guidelines that Justin 2.0 will provide. If you have any questions at all, feel free to email be at my personal email justinthedev@outlook.com.

# Table of contents:

- [Simple Edits](#simple-edits)
    - [Editor Page](#editor-page)
    - [Content Manager / Dynamic Content](#content-manager--dynamic-content)
- [Complex Edits (For Web Devs/Designers)](#complex-edits-for-web-devsdesigners)
    - [Countdown](#countdown)
    - [Sponsor Form](#sponsor-form)
    - [Dependencies / Agenda](#dependencies--agenda)

# Simple Edits

## Editor Page

If you follow this link on your **computer** [https://www.spacelawlab.com/?edit=1](https://www.spacelawlab.com/?edit=1) you will be taken to an editor page that looks like this

![Untitled](Space%20Beach%20Law%20Lab%20Web%20Documentation%2038b9383bce05436992c1733e36abd6e7/Untitled.png)

From here you can change much of the text and content on the website — easily. 

Simply click on what you want to change, and then type what you want. This works much like WIX or Squarespace.

![Untitled](Space%20Beach%20Law%20Lab%20Web%20Documentation%2038b9383bce05436992c1733e36abd6e7/Untitled%201.png)

The only thing you **cannot change** is CMS items. CMS items will have a purple outline when hovered.

Also, If you want to change spacing or any design aspects — you must go into the designer — which I do not recommend for non-developers/designers.

## Content Manager / Dynamic Content

Navigate to the *collections page.*

![Untitled](Space%20Beach%20Law%20Lab%20Web%20Documentation%2038b9383bce05436992c1733e36abd6e7/Untitled%202.png)

Now that we are at the *collections* page you will see a list of collections. 

**Collection’s** are simply a collection of a given object.. for example our event had several events — several speakers — and several sponsors. The cool thing about this is the website is designed in a way where when you add and **event** or a **speaker** it automatically will add it to website and style it.

Now, click the speakers collection and click the big green button on the top that reads: “**+ new speaker”.**

Now you will see a simple form. I tried to make each field as descriptive as possible for anyone to fill out.

![Untitled](Space%20Beach%20Law%20Lab%20Web%20Documentation%2038b9383bce05436992c1733e36abd6e7/Untitled%203.png)

Once you are done, click create and a speaker will be *ready* to be added to the website.

To actually add the speaker you must publish the website

# Complex Edits for Web Devs

## Countdown Timer Logic

There is a timer on the website that counts down to the event date. To modify the date do the following. 

- Click the Stat-section
- Click Stats wrapper
- Click timer-logic
- On the right panel — click open code editor

![Untitled](Space%20Beach%20Law%20Lab%20Web%20Documentation%2038b9383bce05436992c1733e36abd6e7/Untitled%205.png)

- Simply change the `date` variable to reflect the date you want to count down to. And that's it!

## Sponsor Form

### **If you want to change the automatic emailing when submitting the sponsor form read here.**

The first thing it does is send automatic response emails to the submitter. 

- I used an API called emailjs. I advise you to create an account of your own there, it takes only a few seconds
- Now navigate to your pages
- Click home
- Scroll to the custom code section
    - WARNING - Be careful editing the <head> part of this. It is an essential part of some functionality on the website I’ll write about in the next section
- From within the </body> tag you’ll see:

```jsx
<script>
const contactButton = document.querySelector(".contact");
const emailForm = document.querySelector("#email-form");

contactButton.addEventListener("click", () => {
  setTimeout(() => {
    const element = document.querySelector(".f-success-message");
    const isComplete = element.style.display == "block";
    if (isComplete) {
      emailjs.sendForm("service_nwperz6", "template_6529013", emailForm);
    }
  }, 500); // 2000 milliseconds delay (2 seconds)
});
</script>
