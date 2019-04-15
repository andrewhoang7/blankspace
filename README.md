# Blank Space

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
mobile journaling app that serves as a customizeable and secure space to place your thoughts. designed to be safe space for all issues that are going in your life 

### App Evaluation
- **Category:** Journaling/Mental Health
- **Mobile:** Mobile aspect is essential for the instant logging of any behaviour. Individuals will be able to log in to a personal account and write thoughts
- **Story:** Creates a more intimate environment for a person to engage with their feelings and thoughts.
- **Market:** In general, any individual that is able to read and write English can utilize this. Monetization could be derived from a small fixed fee or minimum subscription per month, or possible licensing to group.
- **Habit:** Customers can fit this anytime throughout the day. Ideally, use of app would be instilled as a daily ritual to clear his/her head or make imporant connections between thoughts and feelings.
- **Scope:** Current scope is to create a secure environment for users to write thoughts in a text-based format. 

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User can login
* User can create a new account
* User can stay logged even if they exit app
* User can create a new journal entry
* User can edit past entries
* User can delete entries
* User sees an organized Layout of journal entries
    * Journals: Based on categories of topics
        * Chapters: Categories further down into sections 
* User can search for text


**Optional Stories**

* User can customize environment in settings(i.e. color scheme, font format) 
* User can have text save in real-time (similar to Google Docs)
* User's text/data is encrypted
* User can coordinate journaling with music, either from streaming or fixed playlist set

### 2. Screen Archetypes

* Login Screen
   * User can login
* Registration Screen
   * User can create a new account
* Home Screen
   * User sees an organized Layout of journal entries
* Creation screen
   * User can create a new journal entry
* Edit/Delete screen
   * User can edit past entries
   * User can delete entries
* Search screen
   * User can search for text


### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Profile
* Settings

**Flow Navigation** (Screen to Screen)

* Login Screen
   * --> Home
* Registration Screen
   * --> Home
* Home Screen
   * --> Create/Delete/Edit Screen. Users from home screen will be able to CRUD journal entries
* Creation Screen
   * --> Home (after creation of journal entry)
* Search Screen 
   * --> None


## Wireframes
<img src="https://drive.google.com/uc?id=1X05hddYQgSJSX0pIEb6X_oZDy-6p94z3" width=600>


## Schema 
### Models
| Propert       | Type          | Description  |
| ------------- |:-------------:| -----:       |
| journalid     | String        | unique id for journal entry |
| subject       | String        | Subject title of journal entry |
| content       | String        |  actual content of journal entry |
| createdAt     | DateTime      | date when post is created (default field) |
| updatedAt     | DateTime      | date when post is last updated (default field) |



* Profile Screen
   * -->(Read/GET) Query logged in user object
   * -->(Update/PUT) Update user profile image

* Home Screen
   * -->Read/GET
let query = PFQuery(className:"JournalEntry")
query.whereKey("JournalEntry", equalTo: currentUser)
query.order(byDescending: "createdAt")
query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
    if let error = error {
        print(error.localizedDescription)
    } else if let posts = posts {
        print("Successfully retrieved \(posts.count) posts.")
        // TODO: Do something with your journal entries
    }
}

* Create Post Screen
   * -->(Create/POST) Create a new post object
