.. _lv_dropdown:

=======================================
Drop-down list（下拉列表）(lv_dropdown)
=======================================

Overview（概述）
****************

.. raw:: html

   <details>
     <summary>显示原文</summary>

The drop-down list allows the user to select one value from a list.

The drop-down list is closed by default and displays a single value or a
predefined text. When activated (by click on the drop-down list), a list
is created from which the user may select one option. When the user
selects a new value, the list is deleted again.

The Drop-down list is added to the default group (if one is set).
The Drop-down list is an editable Widget allowing list-item selection via
encoder or keyboard navigation as well.

.. raw:: html

   </details> 
   <br>


下拉列表允许用户从选项列表中选择一个值。

下拉列表的选项表默认是关闭的，其中的选项可以是单个值或预定义文本。 当单击下拉列表后，其将创建一个列表，用户可以从中选择一个选项。 当用户选择了一个值后，该列表将被删除，下次点击会再重新生成。

下拉列表被添加到默认组（如果已设置默认组的话）。
下拉列表是一个可编辑的部件，它也允许通过编码器或键盘导航来进行列表项的选择。

.. _lv_dropdown_parts_and_styles:

Parts and Styles（部分和样式）
****************************

.. raw:: html

   <details>
     <summary>显示原文</summary>

The Dropdown widget is built from the elements: "button" and "list"
(both not related to the button and list widgets)

.. raw:: html

   </details> 
   <br>


下拉组件由以下元素组成：“按钮”和“列表”（都与按钮和列表控件无关，也就是并不是按钮和列表控件）


Button（按钮）
-------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

-  :cpp:enumerator:`LV_PART_MAIN` Background of button, uses the typical
   background- and text-properties for its text.
-  :cpp:enumerator:`LV_PART_INDICATOR` Typically an arrow symbol that can be an Image
   or text (e.g. :cpp:enumerator:`LV_SYMBOL`).

The button goes to :cpp:enumerator:`LV_STATE_CHECKED` when it's opened.

.. raw:: html

   </details> 
   <br>


-  :cpp:enumerator:`LV_PART_MAIN`：按钮的背景部分，其文本会使用典型的背景属性和文本属性。
-  :cpp:enumerator:`LV_PART_INDICATOR`：通常是一个箭头符号，可以是图片或文本形式（例如 :cpp:enumerator:`LV_SYMBOL`）

按钮在打开时，会设置为 :cpp:enumerator:`LV_STATE_CHECKED` 状态。


List（列表）
------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

-  :cpp:enumerator:`LV_PART_MAIN` The list itself. Uses the typical background
   properties. ``max_height`` can be used to limit the height of the
   list.
-  :cpp:enumerator:`LV_PART_SCROLLBAR` The scrollbar background, border, shadow
   properties and width (for its own width) and right padding for the
   spacing on the right.
-  :cpp:enumerator:`LV_PART_SELECTED` Refers to the currently pressed, checked or
   pressed+checked option. Also uses the typical background properties.

The list is hidden/shown on open/close. To add styles to it use
:cpp:expr:`lv_dropdown_get_list(dropdown)` to get the list object. For example:

.. code:: c

   lv_obj_t * list = lv_dropdown_get_list(dropdown) /*Get the list*/
   lv_obj_add_style(list, &my_style, selector)      /*Add the styles to the list*/

Alternatively the theme can be extended with the new styles.

.. raw:: html

   </details> 
   <br>


-  :cpp:enumerator:`LV_PART_MAIN` 列表本身。 使用典型的背景属性。可通过设置 ``max_height`` 限制列表的高度。
-  :cpp:enumerator:`LV_PART_SCROLLBAR` 列表滚动条的背景、边框、阴影属性和宽度（对于它自己的宽度）以及右侧间距的右侧填充。
-  :cpp:enumerator:`LV_PART_SELECTED` 指的是当前按下、选中或按下+选中的选项。 也是使用典型的背景属性。

列表在打开或关闭时会隐藏或显示。若要向其添加样式，请使用 :cpp:expr:`lv_dropdown_get_list(dropdown)` 获取列表对象。例如：

.. code:: c

   lv_obj_t * list = lv_dropdown_get_list(dropdown) /*Get the list*/
   lv_obj_add_style(list, &my_style, selector)      /*Add the styles to the list*/

或者，可以使用自定义新样式扩展主题。


.. _lv_dropdown_usage:

Usage（用法）
************

.. _lv_dropdown_options:

Options（选项）
***************

List items（列表选项）
----------------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

The list items are passed to the Drop-Down List as a newline-separated list in a string
as the ``options`` argument to :cpp:expr:`lv_dropdown_set_options(dropdown, options)`.
Each list item should be separated by ``\n``.  Example: ``"First\nSecond\nThird"``.
This string is copied by the Drop-Down List, so its contents do not need to remain
available beyond this call.

The :cpp:expr:`lv_dropdown_add_option(dropdown, "New option", pos)` function
inserts a new option at index ``pos``.

To save memory the options can set from a static(constant) string too
with :cpp:expr:`lv_dropdown_set_static_options(dropdown, options)`. In this case
the options string should be alive while the drop-down list exists and
:cpp:func:`lv_dropdown_add_option` can't be used

You can select an option manually with
:cpp:expr:`lv_dropdown_set_selected(dropdown, id)`, where ``id`` is the index of
an option.

.. raw:: html

   </details> 
   <br>


列表项作为一个以换行符分隔的字符串列表，通过 :cpp:expr:`lv_dropdown_set_options(dropdown, options)` 函数的 ``options`` 参数传递给下拉列表。每个列表项应该用 ``\n`` 分隔。例如： ``"First\nSecond\nThird"``。这个字符串会被下拉列表复制，所以在此调用之后，其内容无需保持可用状态。

:cpp:expr:`lv_dropdown_add_option(dropdown, "New option", pos)` 函数可在索引 ``pos``处插入一个新的选项。

为了节省内存，选项也可以使用函数 :cpp:expr:`lv_dropdown_set_static_options(dropdown, options)` 从静态（常量）字符串中设置。 在这种情况下，当下拉列表存在时，选项字符串应该处于活动状态，并且不能使用 :cpp:func:`lv_dropdown_add_option` 插入新的选项。

可以使用 :cpp:expr:`lv_dropdown_set_selected(dropdown, id)` 手动选择一个选项，其中 ``id`` 是一个选项的索引，选项从 0 开始索引。


Get selected option（获取选择的选项）
------------------------------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

The get the *index* of the selected option, use
:cpp:expr:`lv_dropdown_get_selected(dropdown)`.

:cpp:expr:`lv_dropdown_get_selected_str(dropdown, buf, buf_size)` copies the
*name* of the selected option to ``buf``.

.. raw:: html

   </details> 
   <br>


要获取所选中的选项的索引（index），使用函数 :cpp:expr:`lv_dropdown_get_selected(dropdown)`。

要获取所选中的选项的文本（str），使用函数 :cpp:expr:`lv_dropdown_get_selected_str(dropdown, buf, buf_size)`  将所选选项的 *name* 复制到 ``buf``。


Direction（方向）
----------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

The list can be created on any side. The default :cpp:enumerator:`LV_DIR_BOTTOM` can
be modified by :cpp:expr:`lv_dropdown_set_dir(dropdown, LV_DIR_LEFT)` function.

If the list would be vertically out of the screen, it will be aligned to
the edge.

.. raw:: html

   </details> 
   <br>


列表可以在任何一侧创建（展开）。 默认是 :cpp:enumerator:`LV_DIR_BOTTOM` （底部展开），可以通过函数 :cpp:expr:`lv_dropdown_set_dir(dropdown, LV_DIR_LEFT)` 修改展开方向。

如果列表在指定的展开方向超出的屏幕（父对象）的范围，其会自动进行调整展开方向。


Symbol（符号）
-------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

A symbol (typically an arrow) can be added to the dropdown list with
:cpp:expr:`lv_dropdown_set_symbol(dropdown, LV_SYMBOL_...)`

If the direction of the drop-down list is :cpp:enumerator:`LV_DIR_LEFT` the symbol
will be shown on the left, otherwise on the right.

.. raw:: html

   </details> 
   <br>


可以使用函数 :cpp:expr:`lv_dropdown_set_symbol(dropdown, LV_SYMBOL_...)` 将符号（通常是箭头）添加到下拉列表中

如果下拉列表的方向是 :cpp:enumerator:`LV_DIR_LEFT` ，符号将显示在左侧，否则显示在右侧，上下侧类似。


Show selected（显示选中）
------------------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

The main part can either show the selected option or a static text. If a
static is set with :cpp:expr:`lv_dropdown_set_text(dropdown, "Some text")` it
will be shown regardless to th selected option. If the text is ``NULL``
the selected option is displayed on the button.

.. raw:: html

   </details> 
   <br>


主要部分(LV_PART_MAIN)可以显示所选选项或静态文本。 如果使用函数 :cpp:expr:`lv_dropdown_set_text(dropdown, "Some text")` 设置内容，那么无论选择哪个选项，它都会只会显示你所设置的内容。 如果文本为 ``NULL``，则所当前选选项将显示在按钮上。


Programmatically open/close（编程打开或关闭）
---------------------------------------------

.. raw:: html

   <details>
     <summary>显示原文</summary>

To programmatically open or close the Drop-Down List use
:cpp:expr:`lv_dropdown_open(dropdown)` or :cpp:expr:`lv_dropdown_close(dropdown)`.

.. raw:: html

   </details> 
   <br>


要通过编程方式打开或关闭下拉列表，可以使用 :cpp:expr:`lv_dropdown_open(dropdown)`或 :cpp:expr:`lv_dropdown_close(dropdown)`。

.. _lv_dropdown_events:

Events（事件）
*************

.. raw:: html

   <details>
     <summary>显示原文</summary>

Apart from the `Generic events <../overview/event.html#generic-events>`__, the following
`Special events <../overview/event.html#special-events>`__ are sent by
the drop-down list:

- :cpp:enumerator:`LV_EVENT_VALUE_CHANGED` Sent when the new option is selected or the list is opened/closed.
- :cpp:enumerator:`LV_EVENT_CANCEL` Sent when the list is closed
- :cpp:enumerator:`LV_EVENT_READY` Sent when the list is opened

See the events of the :ref:`Base object <lv_obj>` too.

Learn more about :ref:`events`.

.. raw:: html

   </details> 
   <br>


除了 `通用事件 <../overview/event.html#generic-events>`__ ，下拉列表还可以发送以下 `特殊事件 <../overview/event.html#special-events>`__  ：

- :cpp:enumerator:`LV_EVENT_VALUE_CHANGED` 在选择新选项或打开/关闭列表时发送。
- :cpp:enumerator:`LV_EVENT_CANCEL` 列表关闭时发送
- :cpp:enumerator:`LV_EVENT_READY` 打开列表时发送

可以参考 :ref:`Base object <lv_obj>` 的事件。

详细了解更多 :ref:`events`。


.. _lv_dropdown_keys:

Keys（按键）
***********

.. raw:: html

   <details>
     <summary>显示原文</summary>

-  ``LV_KEY_RIGHT/DOWN`` Select next list item.
-  ``LV_KEY_LEFT/UP`` Select previous list item.
-  :cpp:enumerator:`LV_KEY_ENTER` Apply selected list item (sends
   :cpp:enumerator:`LV_EVENT_VALUE_CHANGED` event and closes Drop-Down List).

.. admonition::  Further Reading

    Learn more about :ref:`indev_keys`.

.. raw:: html

   </details> 
   <br>


-  ``LV_KEY_RIGHT/DOWN``：选择下一个列表项。
-  ``LV_KEY_LEFT/UP``：选择上一个列表项。
-  :cpp:enumerator:`LV_KEY_ENTER`：应用所选的列表项（会发送  :cpp:enumerator:`LV_EVENT_VALUE_CHANGED` 事件并关闭下拉列表）。

.. admonition::  Further Reading

    进一步了解:ref:`indev_keys`。


.. _lv_dropdown_example:

Example
*******

.. include:: ../examples/widgets/dropdown/index.rst

.. _lv_dropdown_api:

API
***
