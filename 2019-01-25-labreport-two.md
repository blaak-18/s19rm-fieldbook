---
layout: post
title: "LAB REPORT TWO"
tags: [lab report, fieldbook]
author: AVERY BLANKENSHIP
---
-------------------

### Lab Report Week Two
-

_**Prompt:**_
For this lab report, I want you to do two things. First, to reflect as always on the lab we conducted together. How does working by candlelight help you think about early practices of textual production and the codex format? What new insights are produced by the experience?

Second, I would ask you to choose another format: perhaps something more contemporary, such as a software format, or something related to your own area of research interest. Then, I would ask you to consider—and this might require some brief additional research—a technical or material element that influences the form, production, or use of your format. You have latitude here, but you should be considering something that seems on first glance to stand apart from the content of your format, as the candle perhaps seems separate from the content of the manuscripts produced by its light. What new insight might we glean by considering these elements together, or by widening our lens from a given medium to the technologies or materials central to its expression?

-

_**Response:**_

Even as someone very interested in nineteenth century texts, I had never really considered (or put myself in the shoes of) someone who practices textual production. Working by candlelight for this lab required not only a physical closeness with the next because the dim light made it difficult to distinguish what was on the page, but the darkness of the room around me provided me with an otherworldliness that I'm not sure I've experienced before. Even though I was surrounded by other people, that single pinprick of light by my hand had a way of making me feel entirely alone. It almost felt like it had been some time since I had been alone in that way with a text.

Once the initial wonder wore off (and it did so quickly) I became increasingly aware of the physical pain in my body. Holding a pencil can be difficult for me because of my disibility and I have poor vision, already, and so I couldn't help but to think about the ways that reading and writing as physical labor have changed over time. In some ways, I was reminded of “Farewell etaoin shrdlu” and how so much of the documentary seemed to focus on how sad it is to lose these technologies that we feel nostalgia for, but in the case of hand transcribing by candlelight, I became incredibly grateful that technology has evolved beyond that method. What must it have been like to have a physical disability or poor vision in the nineteenth century? How painful must that have been? And then, for that to be the only way.

Amaranth Borsuk writes about how "the book" and writing, in general, has evolved around the changing needs of humans and that often, technologies of the book can be shaped by the physical limitations of the objects being used (in the case of Chinese jiance). When thinking about the second part of the prompt, my thoughts went to the way that programming and coding works when compared to writing by candlelight. Below, I've included a snippet of Python code that I wrote for my work with Viral Texts. I started to think about the ways that this programming language works and how the "tab" key and "spacebar" on a keyboard influences the way that the language operates. Unlike some other programming languages, in Python, indentions and spaces matter quite a bit. In fact, I think that this makes Python quite different from even written languages. The indentions are so important to the function of the language, that if the code is aligned properly (a tab is equal to exactly five spaces), then the program simply wont run.

Take this for example:
```
def account():
    form = UpdateAccountForm()
    if form.validate_on_submit():
        if form.picture.data: #update picture
            picture_file = save_picture(form.picture.data)
            current_user.image_file = picture_file
```
 and this:
 ```
 def account():
     form = UpdateAccountForm()
     if form.validate_on_submit():
      if form.picture.data: #update picture
             picture_file = save_picture(form.picture.data)
             current_user.image_file = picture_file
 ```
Do you see a difference? I can hardly see one, myself. However, the second example has two fewer spaces on the line beginning with "if form.picture.data" which means that the way that the compiler understands the code is completely different.

Here is a more extreme example:
```
def account():
    form = UpdateAccountForm()
    if form.validate_on_submit():
    if form.picture.data: #update picture
    picture_file = save_picture(form.picture.data)
    current_user.image_file = picture_file
```
In this example, when the code is run, because the logic of following the indentions (the least indented things run first) is a huge tenant in Python, this code will all run at the exact same time, rather than follow any order. While other programming languages have other organizing principles, in the example of Python, the major organizing principle has evolved around the tab and spacebar keys being present on the keyboard which forces the programmer to not only be conscious of the things that they *are* typing, but to also become incredibly conscious of the things that *aren't* there, as well. It's hard to think of a "blankness" as a presence, but in this example, the formatting is almost just as much part of the language as the actual words.

Complete snippet:
```
@app.route("/account", methods=['GET', 'POST'])
@login_required
def account():
    form = UpdateAccountForm()
    if form.validate_on_submit():
        if form.picture.data: #update picture
            picture_file = save_picture(form.picture.data)
            current_user.image_file = picture_file
        current_user.username = form.username.data #update username
        current_user.email = form.email.data #update email
        db.session.commit() #save to database
        flash('Your account has been updated!', 'success')
        return redirect(url_for('account')) #get-post redirect --> don't let form resubmit
    elif request.method == 'GET':
        form.username.data = current_user.username #show current username
        form.email.data = current_user.email #show current email
    image_file = url_for('static', filename='profile_pics/' + current_user.image_file) #show current profile pic
    return render_template('account.html', title='Account',
                           image_file=image_file, form=form)

```
