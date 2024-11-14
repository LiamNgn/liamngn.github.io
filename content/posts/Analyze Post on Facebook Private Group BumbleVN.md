---
title: Analyze Post on Facebook Private Group BumbleVN
date: 2024-10-16 11:41:00
lastmod: 2024-11-14 20:19:32
categories:
  - 
tags:
  - 
aliases: 
share: true
---

# Analyze Post on Facebook Private Group BumbleVN

2024-10-21

So in order to scrape the data, I will use Selenium. Without any explanations, all steps in the process will be conducted using selenium. The process will go as follows:

- First, I will login to a Facebook account that allows access to that private Facebook group. In the process of opening the Facebook page, I also need to close the cookie request box.
- Secondly, I go to the link that contains the search result and the filter in our private group. In our case, the group is BumbleVN.
- Finally, I proceed to extract the necessary data from our search result and saved to a json or csv file. The precise data type will be decided later.

2024-11-02

- The scraping was way harder than I expect.
- The original ideas was to scroll till ends then save all the contents after having expanded all the posts. I would like to be able to get the number of reactions and the comments. Nevertheless, when doing it this way, I may be able to get the detailed reactions as Ill as all the comments yet I can't separate the posts, which makes it nearly impossible to handle the long line of text effectively. I need a different strategy.
- As I have discovered that you can go to the separate posts by click on the date (TIL), I have decided to change to another strategy. I would scroll to the end, get all the link to the separate posts. Then each of the posts is saved as a separate HTML file. Handling everything from there will be much easier.
- Another issue arises, the link I get when click on is different from the link that Selenium get. Annoying right? I have theorized that the link needed to be hover over to change to the link to the separate group. I have tried scroll to the end then hover the mouse to every elements. HoIver, it's impossible because the first link is too far away to the end of the scroll. I have to change the scroll function so that each scroll will move the mouse to all the link inside. Any link being hovered before won't be touched again.

2024-11-14

- I have not updated in a while but as of today, the scraping is done. I have managed to get individual link to each post from a search result. For each link, I have managed to get user_name, user_url, post_content, reactions, creation_time, and all comments. I will go over each of these in detail below.
- As I stated above, in order to get the correct link, I have to hover the mouse over. Yet doing it on a large scale is not that easy. I have to get all link on the current view, move the mouse to the link. If some links are not available, I will scroll down for half of the page length then repeat the process again. This also simplify the process because I don't have to scroll up and down to get the link but down only. I manage to get all the links after doing these.
- Getting the user_name, user_url are rather easy. I only have to find the xpath link and get it. The slight inconvenience is the fact that the xpath links to anonymous member and non-anonymous member are different. A simply try-except statement would suffice.
- Due to the fact that post_content may contain a lots of emoji/links, I have to loop over all the div contains the contents and save them in the innerHTML form.
- The reactions is quite difficult because I wanted to get all number of reactions as Ill as number of each reactions. The creation_time is really difficult because at first it seemed like Meta does not really let us get the creation_time. Nevertheless, a simple Google gives us xpath link to a js script which contains a json file. This json file luckily contains the creation_time in term of UNIX time and the individual number of each reaction. There are still a lot more things that can be harvested from this JSON file. The xpath link to this script is `//script[contains(text(), "creation_time")]`
- The comments is the most difficult thing for me. I wanted to get the full content of the comments as Ill as to maintain the hierarchy of the comments. These require expanding all the comments to see the replies as Ill as expand the long comments that by pressing the button 'See more'. The replied comments are easy yet the 'See more' button sometimes can be obscured. I have to determine the position of the ancestor node and go down from there. Maintaining the hierarchy was another tricky part. I have to write classes of comment and tree-like structure to maintain the hierarchy of the comments. It was messy and quite ad-hoc but it works.
- [/] Scraping the data ➕ 2024-10-16
- [ ] Plan how to analyze the data ➕ 2024-10-16
