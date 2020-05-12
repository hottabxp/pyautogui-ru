.. PyAutoGUI documentation master file, created by
   sphinx-quickstart on Sun Jul 20 12:59:43 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to PyAutoGUI's documentation!
=====================================


API разработан таким образом, чтобы быть простым. PyAutoGUI работает в Windows, macOS и Linux, и поддерживает Python 2 и 3.

Для установки, выполните ``pip install pyautogui``. See the :doc:`install` page for more details.

Исходный код доступен по адресу: https://github.com/asweigart/pyautogui

В PyAutoGUI имеются следующие функции:

* Moving the mouse and clicking in the windows of other applications.
* Перемещение и клик мышки в окнах других приложений .
* Отправка нажатий клавиш в приложения( например, для заполнения форм)
* Take screenshots, and given an image (for example, of a button or checkbox), and find it on the screen.
* Locate an application's window, and move, resize, maximize, minimize, or close it (Windows-only, currently).
* Паказывать диалоговые окна для предупреждений и сообщений.

Here's `a YouTube video of a bot automatically playing the game Sushi Go Round <https://www.youtube.com/watch?v=lfk_T6VKhTE>`_. The bot watches the game's application window and searches for images of sushi orders. When it finds one, it clicks the ingredient buttons to make the sushi. It also clicks the phone in the game to order more ingredients as needed. The bot is completely autonomous and can finish all seven days of the game. This is the kind of automation that PyAutoGUI is capable of.

Примеры
========

.. code:: python

    >>> import pyautogui

    >>> screenWidth, screenHeight = pyautogui.size() # Получаем размер экрана.
    >>> screenWidth, screenHeight
    (2560, 1440)

    >>> currentMouseX, currentMouseY = pyautogui.position() # Получаем XY координаты курсора.
    >>> currentMouseX, currentMouseY
    (1314, 345)

    >>> pyautogui.moveTo(100, 150) # Перемещение курсора по координатам XY.

    >>> pyautogui.click()          # Клик мышки.
    >>> pyautogui.click(100, 200)  # Перемещение мышки по XY координатам и клик по ним.
    >>> pyautogui.click('button.png') # Поиск на экране совпадение с button.png и клик по нему.

    >>> pyautogui.move(400, 0)      # Перемещение мышки вправо от текущей позиции на 400 пикселей
    >>> pyautogui.doubleClick()    # Двойной клик.
    >>> pyautogui.moveTo(500, 500, duration=2, tween=pyautogui.easeInOutQuad)  # Use tweening/easing function to move mouse over 2 seconds.

    >>> pyautogui.write('Hello world!', interval=0.25)  # Печатаем текст с паузой в четверть секунды для каждого нажатия клавиши.
    >>> pyautogui.press('esc')     # Нажимаем клавишу ESC. Имена всех клавиш в pyautogui.KEY_NAMES

    >>> pyautogui.keyDown('shift') # Нажимаем и удерживаем клавишу SHIFT.
    >>> pyautogui.press(['left', 'left', 'left', 'left']) # Нажимаем клавишу ВЛЕВО 4 раза.
    >>> pyautogui.keyUp('shift')   # Отпускаем клавишу SHIFT.

    >>> pyautogui.hotkey('ctrl', 'c') # Нажимаем комбинацию Ctrl-C.

    >>> pyautogui.alert('This is the message to display.') # Создаем диалоговое окно с предупреждением, и приостанавливаем программу, пока не нажата кнопка 'OK'

Этот пример перемещает мышь в виде квадратной спирали в MS Paint(или любой другой программе для рисования)

.. code:: python

    >>> distance = 200
    >>> while distance > 0:
            pyautogui.drag(distance, 0, duration=0.5)   # двигаем вправо
            distance -= 5
            pyautogui.drag(0, distance, duration=0.5)   # двигаем вниз
            pyautogui.drag(-distance, 0, duration=0.5)  # двигаем влево
            distance -= 5
            pyautogui.drag(0, -distance, duration=0.5)  # двигаем вверх

.. image:: square_spiral.png

The benefit of using PyAutoGUI, as opposed to a script that directly generates the image file, is that you can use the brush tools that MS Paint provides.

FAQ: Frequently Asked Questions
===============================

Send questions to al@inventwithpython.com

**Q: Can PyAutoGUI work on Android, iOS, or tablet/smartphone apps.**

A: Unfortunately no. PyAutoGUI only runs on Windows, macOS, and Linux.

**Q: Does PyAutoGUI work on multi-monitor setups.**

A: No, right now PyAutoGUI only handles the primary monitor.

**Q: Does PyAutoGUI do OCR?**

A: No, but this is a feature that's on the roadmap.

**Q: Can PyAutoGUI do keylogging, or detect if a key is currently pressed down?**

A: No, PyAutoGUI cannot do this currently.


Fail-Safes
==========

.. image:: sorcerers_apprentice_brooms.png

Like the enchanted brooms from the Sorcerer’s Apprentice programmed to keep filling (and then overfilling) the bath with water, a bug in your program could make it go out of control. It's hard to use the mouse to close a program if the mouse cursor is moving around on its own.

As a safety feature, a fail-safe feature is enabled by default. When a PyAutoGUI function is called, if the mouse is in any of the four corners of the primary monitor, they will raise a ``pyautogui.FailSafeException``. There is a one-tenth second delay after calling every PyAutoGUI functions to give the user time to slam the mouse into a corner to trigger the fail safe.

You can disable this failsafe by setting ``pyautogui.FAILSAFE = False``. **I HIGHLY RECOMMEND YOU DO NOT DISABLE THE FAILSAFE.**


Contents:

.. toctree::
   :maxdepth: 2

   install.rst
   quickstart.rst
   mouse.rst
   keyboard.rst
   msgbox.rst
   screenshot.rst
   tests.rst
   roadmap.rst

   source/modules.rst

This documentation is still a work in progress.


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

