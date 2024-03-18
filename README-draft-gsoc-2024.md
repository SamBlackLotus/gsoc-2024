"Creating a brazilian Boilerplate of a digital participation Platform" proposal for
Google Summer of Code 2024.

Table of content
================

1. **Abstract** 1.1 Drawbacks of the existing GUI framework 1.2 Goals 1.3 Benefits
2. **The new framework** 2.1 Overview 2.2 Advantages
3. **Schedule and milestones** 3.1 Prepare the field 3.2 Port Cricket to use Toga 3.3 Usage documentation 3.4 If time permits...
4. **About me**

# 1 Abstract

## 1.1 Drawbacks of the existing GUI framework

Cricket's GUI interface is currently implemented using Tkinter, which has a lot of limitations. For example: Tkinter has no built-in table widget, while Toga does. Tkinter does not support CSS properties for styling the objects, while Toga supports because of the Colosseum framework, the (partial) implementation of the CSS box and the flexbox layout algorithm. Also, the Toga project is very active, the community is always developing and fixing issues, and looks / feels like a native app for multiple platforms.


## 1.2 Goals

The main goal is the complete port of Cricket to use Toga as the framework for GUI interface. The base logic is mostly complete, so firstly I will plan how to adapt the actual architecture of the view to use Toga widgets. If I find one widget that Cricket uses but isn't implemented on Toga, I will develop a contribution to this specific widget. This way the application will not lose the basics layout.

So, the proposal will not only focus on the port of Tkinter to Toga, but on mapping the necessary widgets for a real application using Toga framework.


## 1.3 Benefits

In addition of the advantages of using Toga instead of Tkinter as I highlighted on section 1.1, this is a opportunity to improve error handling and make better use of features that Toga has but Tkinter does not. It will be the first BeeWare project that “eats it is own dogwood".


# 2 The new framework

## 2.1 Overview

The application logic core will be preserved, migrating only the objects of Tkinter to Toga widgets. Both Tkinter and Toga are event oriented so a redesign of the architecture will not happen.

Example of a simple migration of a widget object of Tkinter to Toga:


Tkinter:
```
  self.toolbar = Frame(self.root)
  self.toolbar.grid(column=0, row=0, sticky=(W, E))

  self.stop_button = Button(self.toolbar,
                            text='Stop',
                            command=self.cmd_stop,
                            state=DISABLED)
  self.stop_button.grid(column=0, row=0)
```

Toga:
```
  box = toga.Box()

  self.stop_button = toga.Button('Stop', on_press=self.cmd_stop, enabled=False)
  button.style.set(width=100, margin_left=10)

  box.add(button)
```


## 2.2 Advantages

At the example above we can already see the first advantage of the migration, the CSS usage, allowing more flexibility of the UI design. Also there are widgets that exist only in Toga, like the Table widget. More features can be added from this migration.


# 3 Schedule and milestones

I am going to two events during the GSOC, one during June 15th-18th and one during the period August 1st-5th. But these events are academic and will not prevent me from working there.

Also, it is important to cite the days that I will probably work half of the time because of the exams I will have on college:

- June 1, 12, and 29
- July 5, 6


## 3.1 Prepare the field -- first milestone (1 week)

(From May 30 until June 5)

Before starting coding there are a few important things to do around the first week:

- Learn the architecture of Tkinter and Toga
- Review alongside the mentor what is important to maintain from the base code
- Which parts parts of Cricket would be good to add new features from Toga


## 3.2 Port Cricket to use Toga -- second milestone (9 weeks)

(From June 6 until August 7)

Each part of this milestone will follow a development process cycle: build, test and document.  I will focus only on the Cocoa platform on each improvement or development of widgets on Toga. All modifications on Cricket will be made on the files [view.py](https://github.com/pybee/cricket/blob/master/cricket/view.py) and on [main.py](https://github.com/pybee/cricket/blob/master/cricket/main.py). For Toga, the additions/modifications will be made on [widgets](https://github.com/pybee/toga/tree/master/src/cocoa/toga_cocoa/widgets) folder.

To elaborate this section of the proposal I mapped each object used with Tkinter that exists in Toga, some objects need to be explored with more details but the next sub sections will focus on solving the development on a top-down view, solving the "easiest" problems first, such as adapting the complete widgets that exist on Toga already and is used on Cricket.

Aside from modifying the main file, since the GUI is separated on an independent class named ``MainWindow``, there is no need to refactor any other class when the port is complete.

The average time cost to develop a widget was calculated from the time cost that the primary author from the Cricket project, Russell Keith-Magee, developed some new widget or feature to a specific platform (inferred from commits on GitHub), multiplied by 6 to estimate the time that I will take to develop.

### 3.2.1 Adapt the complete widgets that exist on Toga already and is used on Cricket (4 weeks)

#### 3.2.1.1 Core Widgets (1.5 week)

The core widgets available on Toga are ``Application``, ``Box``, ``Font``, ``Widget`` and ``Window``, but I will need to adapt only 4 of them, since the utility of the class ``Widgets`` on Cricket will be defined later on ``Tree``. The explanation is the following:

- Application

Toga: This core widget is used to manage the main loop of the application and to control the other core widget, Window, setting the title, size and other properties of the main Window.

Tkinter: The title, geometry and other properties of the window on Tkinter also is setup on a core widget of the application, named root.

Result: This adaptation is possible.

- Box

Toga: Box is a container for any widget, so other boxes can be added inside it as well. Also, with the Colosseum integration, the style is made with a partial CSS environment.

Tkinter: The closest similar object of ``Box`` on this framework would be the ``PanedWindow``, which allows add other panes inside a bigger pane and modify the styles. The ``Frame`` widget is also similar.

Result: This adaptation is possible.

- Font

Toga: Fonts of the labels, modify family and size.

Tkinter: Also allows to modify de family and size, but there are many other options, like, weight, underline, overstrike and slant.

Result: Since is not really necessary to add weight of label this adaptation is possible. If time permits I can add those new properties on Toga.

- Widget

Toga: Base class for widgets, not instantiated directly.

Tkinter: Standard options and commands supported on all widgets. This module is used on Cricket as a event handler when a test case has been selected in the tree.

Result: These event handler explained above will be develop on another widget, ``Tree``. So the adaptation will be made later.

- Window

Toga: Display components to the user, support displaying multiple widgets, toolbars and resizing.

Tkinter: The class more similar to ``Window`` is the ``Frame`` together with the main class ``Tk``. Then you can set the title on root window, add multiple widgets, toolbar and also resize.

Result: This adaptation is possible.

- Number Input

Toga: Text input box that is limited to numeric input.

Tkinter: Similar to this class there is ``Entry``, but it is a editable text field widget, not only for number. We'll adapt this kind of widget on ``Text Input``.

Result: There is no need to adapt this widget.

##### 3.2.1.2 General Widgets (3 weeks)

The general widgets available on Toga are ``Button``, ``Image View``, ``Label``, ``Multiline Text Input``, ``Number Input``, ``Option Container``, ``Progress Bar``, ``Selection``, ``Text Input``, ``Table`` and ``Tree``, but I'll need adapt only 6 of them.  I propose work on 2 widgets per week. The widgets that were cut off from adaptation are the following:

- Image View

Toga: Container for an image to be rendered on the display.

Tkinter: Cricket doesn't use this feature.

Result: There is no need to adapt this widget.

- Multiline Text Input

Toga: Similar to the text input but designed for larger inputs, similar to the text area field of HTML.

Tkinter: Cricket doesn't use this feature.

Result: There is no need to adapt this widget.

- Selection

Toga: A simple control for allowing the user to choose between a list of string options.

Tkinter: The class similar to this widget is ``OptionMenu``, but Cricket doesn't use it.

Result: There is no need to adapt this widget.

- Table

Toga: Display tabular data. It can be instantiated with the list of headings and then data rows can be added.

Tkinter: Doesn't exist this widget on Tkinter.

Result: There is no need to adapt this widget.

###### 3.2.1.2.1 Basic General Widgets (1 week) 

- Button

Toga: Basic clickable button. It's possible to modify the label, event on press, state of disable or enable.

Tkinter: On Cricket the button of Tk is used with the same features that the button on Toga offers.

Result: This adaptation is possible.

- Label

Toga: A text-label for annotating forms or interfaces.

Tkinter: On Cricket the label of Tk is used with the same features that the label on Toga offers.

Result: This adaptation is possible.

###### 3.2.1.2.1 Intermediate General Widgets (1 week) 

- Text Input

Toga: A simple input field for user entry of text data.

Tkinter: On Tkinter this widget will have 2 utilities, first to substitute ``Entry`` and second ``ReadOnlyText`` because there is a ``set_readonly`` method.

Result: This adaptation is possible.

- Progress Bar

Toga: Simple widget for showing a percentage progress for task completion.

Tkinter: The important properties of ``Progress Bar`` are to set the value and the max to go. There are other properties that this widget have in addition on Tkinter, for example, length, orientation and mode.

Result: The basic implementation of this widget on Toga are enough to adapt on Cricket even without those properties that Tkinter has in advance.

###### 3.2.1.2.1 Advance General Widgets (1 week) 

- Option Container

Toga: Is a user-selection control for choosing from a pre-configured list of controls, like a tab view.

Tkinter: There is the class for this on Tkinter, the ``Notebook``, that is a multi-paned container widget.

Result: The object of Tkinter is used on Cricket with the same properties that are available on Toga, so this adaptation is possible.

- Tree

Toga: A scrollable display of heirarchical data.

Tkinter: Hierarchical multicolumn data display widget.

Result: This adaptation is possible.

##### 3.2.1.3 Layout Widgets (1.5 week)

The layout widgets available on Toga are ``Scroll Container``, ``Split Container`` and ``Web View``, but I will need adapt only 2 of them. The explanation is the following:

- Scroll Container

Toga: Similar to the iframe or scrollable div element in HTML, it contains an object with its own scrollable selection.

Tkinter: Control the viewport of a scrollable widget.

Result: The final use of these two widget are the same, but the difference is that on Toga you add content on a scroll container and on Tkinter you add a scroll bar on a container, so this adaptation is possible.

- Split Container

Toga: Is a container with a movable split and the option for 2 or 3 elements.

Tkinter: There is no similar widget on Tkinter like ``Split Container`` but on Cricket are simulate using two separated ``Frames``.

Result: This adaptation is possible.

- Web View

Toga: Displaying an embedded browser window within an application.

Tkinter: Cricket doesn't use this feature.

Result: There is no need to adapt this widget.


#### 3.2.2 Improvement of simple widgets on Toga (0.5 week)

There is another widget that Cricket uses on its default layout called ``Checkbutton``. The ``Button`` that is present on Toga does not allow yet to set different stylesheets, so I will add a set style button type using ``NSButton`` class.


####  3.2.3 Development of objects that exist on Cricket but still not implement on Toga (2 weeks)

The ``Menu`` class is used on Cricket but on Toga this widget does not exist yet, so it will be built. There is a setup of the default menu items of a window on [app.py](https://github.com/pybee/toga/blob/master/src/cocoa/toga_cocoa/app.py) file but since this is configurated on the main loop startup, more options can not be added, so the proposal is to create a widget to modify or add new items on the menu. The classes on Cocoa to create this widget are ``NSMenu`` and ``NSMenuItem``.


#### 3.2.4 Finishing port (0.5 week)

- Update [releases](https://github.com/pybee/cricket/blob/master/docs/releases.rst) file.
- Update [authors](https://github.com/pybee/cricket/blob/master/AUTHORS) file.
- Update [roadmap](https://github.com/pybee/cricket/blob/master/docs/internals/roadmap.rst) file.

### 3.3 Usage documentation -- last milestone (2 weeks)

(From August 8 until August 21)

On the [tutorials](https://github.com/pybee/toga/tree/master/docs/tutorial) are presented four basic tutorials of the current widgets and its features, but since we are going to add some new small modifications, it would be interesting to show their usage. For example, the new feature of enable/disable a button.


#### 3.3.2 Add new tutorials with new features for Toga  (1 week)

There are few widgets present on Toga but there are no basics examples on how to use them, so I will include a basic example of each new widgets that I'll develop on 3.2.1. For example, the widget to add menu and menu items proposed on 3.2.1.

If possible, I will add a tutorial for the other widgets that still lack a basic usage example.


### 3.4 If time permits...

There are some TODOs on Cricket, like improving GUI interface, including keyboard shortcuts and search, so, if time permits I will follow this sequence.


## 4 About me

My name is Dayanne Fernandes da Cunha, I'm an undergraduate student of Bachelor on Computer Science at University of Brasília (UnB), Brazil. My time zone is UTC-3. I program in  Python for at least 3 years, I program also in C, C++, Java and Javascript. This is my very first experience on contribution for a open source project. I've already made 2 PR this month and I loved it!
