.. _lv_checkbox:

================================
Checkbox（复选框） (lv_checkbox)
================================

Overview（概述）
****************

.. raw:: html

   <details>
     <summary>显示原文</summary>

The Checkbox Widget is created from a "tick box" and a label. When the
Checkbox is clicked the tick box is toggled.

.. raw:: html

   </details> 
   <br>


复选框 (Checkbox) 控件是由“勾选框”（tick box）和标签（label）组成的。当 Chackbox 被点击时，勾选框会进行切换。


.. _lv_checkbox_parts_and_styles:

Parts and Styles（部分和样式）
*****************************

.. raw:: html

   <details>
     <summary>显示原文</summary>

-  :cpp:enumerator:`LV_PART_MAIN` The is the background of the Checkbox and it uses
   the text and all the typical background style properties.
   ``pad_column`` adjusts the spacing between the tickbox and the label
-  :cpp:enumerator:`LV_PART_INDICATOR` The "tick box" is a square that uses all the
   typical background style properties. By default, its size is equal to
   the height of the main part's font. Padding properties make the tick
   box larger in the respective directions.

The Checkbox is added to the default group (if it is set).

.. raw:: html

   </details> 
   <br>


-  :cpp:enumerator:`LV_PART_MAIN` 这是复选框的背景，它使用文本和所有典型的背景样式属性。 ``pad_column`` 调整复选框和标签之间的间距
-  :cpp:enumerator:`LV_PART_INDICATOR` “勾选框”是一个使用所有典型背景样式属性的正方形。 默认情况下，它的大小等于主要部分字体的高度。 填充属性使复选框在相应方向上变大。

复选框将添加到默认组（如果已设置）。


.. _lv_checkbox_usage:

Usage（用法）
*************

Text（文本）
------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

The text can be modified with the
:cpp:expr:`lv_checkbox_set_text(cb, "New text")` function and will be
dynamically allocated.

To set static text, use :cpp:expr:`lv_checkbox_set_text_static(cb, txt)`. This
way, only a pointer to ``txt`` will be stored.  The provided text buffer must remain
available for the life of the Checkbox.

.. raw:: html

   </details> 
   <br>


文本可以使用 :cpp:expr:`lv_checkbox_set_text(cb, "New text")` 函数进行修改，并将被动态分配。

要设置静态文本，可使用 :cpp:expr:`lv_checkbox_set_text_static(cb, txt)`。通过这种方式，只会存储指向 ``txt`` 的指针。所提供的文本缓冲区在复选框（Checkbox）的整个生命周期内都必须保持可用状态。

Check, uncheck, disable（选中，取消选中，禁用）
---------------------------------------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

You can manually check, un-check, and disable the Checkbox by using the
common state add/clear function:

.. code:: c

   lv_obj_add_state(cb, LV_STATE_CHECKED);   /*Make the checkbox checked*/
   lv_obj_remove_state(cb, LV_STATE_CHECKED); /*Make the checkbox unchecked*/
   lv_obj_add_state(cb, LV_STATE_CHECKED | LV_STATE_DISABLED); /*Make the checkbox checked and disabled*/

To get whether the checkbox is checked or not use:
:cpp:expr:`lv_obj_has_state(cb, LV_STATE_CHECKED)`.

.. raw:: html

   </details> 
   <br>


您可以使用通用状态 添加或清除 功能来手动勾选、取消勾选和禁用复选框：

.. code:: c

   lv_obj_add_state(cb, LV_STATE_CHECKED);   /* 让复选框处于勾选 */
   lv_obj_remove_state(cb, LV_STATE_CHECKED); /* 让复选框不处于勾选 */
   lv_obj_add_state(cb, LV_STATE_CHECKED | LV_STATE_DISABLED); /* 选中并禁用该复选框 */

要了解该复选框是否处于选中状态（若处于选中状态则返回true），请使用：:cpp:expr:`lv_obj_has_state(cb, LV_STATE_CHECKED)`。


.. _lv_checkbox_events:

Events（事件）
*************

.. raw:: html

   <details>
     <summary>显示原文</summary>

-  :cpp:enumerator:`LV_EVENT_VALUE_CHANGED` Sent when Checkbox is toggled.

.. admonition::  Further Reading

    Learn more about :ref:`lv_obj_events` emitted by all Widgets.

    Learn more about :ref:`events`.

.. raw:: html

   </details> 
   <br>


-  :cpp:enumerator:`LV_EVENT_VALUE_CHANGED`：当复选框（Checkbox）被切换时发送该事件。

.. admonition::  Further Reading

    进一步了解所有部件发出的:ref:`lv_obj_events`。

    进一步了解:ref:`events`。


.. _lv_checkbox_keys:

Keys（按键）
************

.. raw:: html

   <details>
     <summary>显示原文</summary>

The following *Keys* are processed by Checkbox:

- ``LV_KEY_RIGHT/UP`` Go to CHECKED state if Checkbox is enabled
- ``LV_KEY_LEFT/DOWN`` Go to non-CHECKED state if Checkbox is enabled
- :cpp:enumerator:`LV_KEY_ENTER` Clicks the Checkbox and toggles its value.

Note that, as usual, the state of :cpp:enumerator:`LV_KEY_ENTER` is translated to
``LV_EVENT_PRESSED/PRESSING/RELEASED`` etc.

.. admonition::  Further Reading

    Learn more about :ref:`indev_keys`.

.. raw:: html

   </details> 
   <br>


以下 “按键（Keys）” 可由复选框（Checkbox）进行处理：

- ``LV_KEY_RIGHT/UP``：如果复选框处于启用状态，则切换至 “已选中（CHECKED）” 状态。
- ``LV_KEY_LEFT/DOWN``：如果复选框处于启用状态，则切换至 “未选中” 状态。
- :cpp:enumerator:`LV_KEY_ENTER`：点击复选框并切换其值。

需要注意的是，和往常一样，:cpp:enumerator:`LV_KEY_ENTER` 的状态会被转换为 ``LV_EVENT_PRESSED/PRESSING/RELEASED`` 等状态。

.. admonition::  Further Reading
    进一步了解:ref:`indev_keys`。


.. _lv_checkbox_example:

Example
*******

.. include:: ../examples/widgets/checkbox/index.rst

.. _lv_checkboxapi:

API
***
