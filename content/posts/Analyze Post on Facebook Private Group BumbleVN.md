---
title: Analyze Post on Facebook Private Group BumbleVN
date: 2024-10-16 11:41:00
lastmod: 2024-11-042 00:1:442:57
categories: 
tags: 
aliases: 
share: true
links: "False"
---

# Analyze Post on Facebook Private Group BumbleVN

[2024-10-21]({{< ref "2024-10-21" >}})

So in order to scrape the data, we will use Selenium. Without any explanations, all steps in the process will be conducted using selenium. The process will go as follows:

- First, we will login to a Facebook account that allows access to that private Facebook group. In the process of opening the Facebook page, we also need to close the cookie request box.
- Secondly, we go to the link that contains the search result and the filter in our private group. In our case, the group is BumbleVN.
- Finally, we proceed to extract the necessary data from our search result and saved to a json or csv file. The precise data type will be decided later.

[2024-11-02]({{< ref "2024-11-02" >}})

- The scraping was way harder than I expect.
- The original ideas was to scroll till ends then save all the contents after having expanded all the posts. We would like to be able to get the number of reactions and the comments. Nevertheless, when doing it this way, we may be able to get the detailed reactions as well as all the comments yet we can't separate the posts, which makes it nearly impossible to handle the long line of text effectively. We need a different strategy.
- As I have discovered that you can go to the separate posts by click on the date (TIL), I have decided to change to another strategy. I would scroll to the end, get all the link to the separate posts. Then each of the posts is saved as a separate HTML file. Handling everything from there will be much easier.
- Another issue arises, the link we get when click on is different from the link that Selenium get. Annoying right? I have theorized that the link needed to be hover over to change to the link to the separate group. I have tried scroll to the end then hover the mouse to every elements. However, it's impossible because the first link is too far away to the end of the scroll. I have to change the scroll function so that each scroll will move the mouse to all the link inside. Any link being hovered before won't be touched again.
- [ ] Scraping the data ➕ 2024-10-16
- [ ] Plan how to analyze the data ➕ 2024-10-16
