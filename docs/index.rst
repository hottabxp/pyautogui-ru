.. PyAutoGUI documentation master file, created by
   sphinx-quickstart on Sun Jul 20 12:59:43 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Добро пожаловать на страницу перевода документации по PyAutoGUI!
=====================================


API разработан таким образом, чтобы быть простым. PyAutoGUI работает в Windows, macOS и Linux, и поддерживает Python 2 и 3.

Для установки, выполните ``pip install pyautogui``. Смотрите страницу :doc:`установки` для получения подробной информации.

Исходный код доступен по адресу: https://github.com/asweigart/pyautogui

В PyAutoGUI имеются следующие функции:

* Перемещение и нажатие кнопок мыши в окнах других приложений .
* Отправка нажатий клавиш в приложения( например, для заполнения форм)
* Делать скриншоты и читать изображения (например, кнопку или чекбокс) и находить его на экране.
* Находить окна приложений, перемещать , изменять размер, максимизировать, минимизировать или закрыть их (на данный момент, только в Windows).
* Показывать диалоговые окна для предупреждений и сообщений.

`Вот видео на YouTybe, как бот играет в игру Sushi Go Round <https://www.youtube.com/watch?v=lfk_T6VKhTE>`_. Бот наблюдает за окном приложения игры и ищет изображения суши-заказов. Когда он находит один, он нажимает на ингредиенты, чтобы сделать суши. Он также кликает по телефону в игре, чтобы заказать больше ингредиентов по мере необходимости. Бот полностью автономный и может завершить все семь дней игры. Это тот вид автоматизации, на который способен PyAutoGUI.

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

    >>> pyautogui.click()          # Клик мыши.
    >>> pyautogui.click(100, 200)  # Перемещение мыши по XY координатам и клик по ним.
    >>> pyautogui.click('button.png') # Поиск на экране совпадение с button.png и клик по нему.

    >>> pyautogui.move(400, 0)      # Перемещение мыши вправо от текущей позиции на 400 пикселей
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

Преимущество использования PyAutoGUI, в отличие от скрипта, который непосредственно генерирует файл изображения, заключается в том, что вы можете использовать инструменты кисти, которые предоставляет MS Paint.

FAQ: Часто задаваемые вопросы:
===============================

Вопросы присылайте на al@inventwithpython.com

**Q: Может ли PyAutoGUI работать на Android, iOS или планшете/телефоне**

A: К сожалению нет. PyAutoGUI работает только на Windows, macOS и Linux.

**Q: Работает ли PyAutoGUI с несколькими мониторами.**

A: Нет, сейчас PyAutoGUI работает только с основным монитором.

**Q: PyAutoGUI распознает символы на изображении(OCR)?**

A: Нет, но это возможно появится в будущем.

**Q: Может ли PyAutoGUI логировать клавиши, или определять, нажата ли клавиша в данный момент?**

A: Нет, PyAutoGUI не может делать это сейчас.


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

