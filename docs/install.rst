.. default-role:: code

============
Установка
============

Чтобы установить PyAutoGUI, установите пакет `pyautogui` из PyPI выполнив `pip install pyautogui` (в Windows) или `pip3 install pyautogui` (в macOS и Linux). (On macOS and Linux, `pip` refers to Python 2's pip tool.)

Инструкции для конкретной ОС приведены ниже.

**ПРИМЕЧАНИЕ. По состоянию на октябрь 2019 года модуль Pillow не поддерживает Python 3.8. PyAutoGUI в настоящее время зависит от этого модуля для его возможностей скриншота.**

Windows
-------

В Windows, вы можете использовать ``py.exe`` для запуска последней версии Python:

    ``py -m pip install pyautogui``

Если у вас установлено несколько версий Python, вы можете выбрать конкретную версию, передав её в командной стороке ``py``. Например, для Python 3.8, выполните:

    ``py -3.8 -m pip install pyautogui``

(Это аналогично команде ``pip install pyautogui``.)

macOS
-----

На macOS и Linux, вам нужно выполнить ``python3``:

    ``python3 -m pip install pyautogui``

Если вы используете El Capitan и у вас проблемы с установкой pyobjc, попробуйте:

    ``MACOSX_DEPLOYMENT_TARGET=10.11 pip install pyobjc``

Linux
-----

В macOS и Linux, вам нужно запустить ``python3``:

    ``python3 -m pip install pyautogui``

В Linux, дополнительно нужно установить приложение ``scrot``, а также Tkinter:

    ``sudo apt-get install scrot``

    ``sudo apt-get install python3-tk``

    ``sudo apt-get install python3-dev``

PyAutoGUI установить зависимые модули, включая PyTweening, PyScreeze, PyGetWindow, PymsgBox, and MouseInfo.
