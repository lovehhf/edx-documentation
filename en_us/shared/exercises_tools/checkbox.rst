.. _Checkbox:

##################
复选框问题
##################

在复选框问题中, 学习者从可能的答案列表中的选择一个或多个选项.为了正确回答问题,学习者必须选择所有正确的选项. 每个复选框问题必须有一个或多个正确选项.

.. image:: ../../../shared/building_and_running_chapters/Images/CheckboxExample.png
 :alt: A checkbox problem with four options, 2 of which are required for the
     correct answer

对于在你课程中的复选框问题,你可以使用edX Insights评估学习者成绩数据和检查提交过的答案. 更多相关信息,请查看： `Using edX Insights`_.

****************************
创建一个复选框问题
****************************

你可以使用简单编辑器或高级编辑器创建复选框问题.你可以在简单编辑器中设置一个问题，然后切换到高级编辑器来添加更多的XML中的配置选项.然而,你不能从高级编辑器切换回简单编辑器。因此,你可能会想要尽可能完全地确定问题的格式在你开始使用先进的编辑器之前。


.. _Use the Simple Editor to Create a Checkbox Problem:

======================================================
使用简单编译器创建复选框问题
======================================================

要使用 :ref:`简单编辑器<简单编辑器>` 创建一个复选框问题,
有以下的步骤.

#. 在你想要创建问题的单元里, 在 **添加新组件** 下方选择 **问题**.
#.  **常见问题类型**, 选择 **复选框**. 添加一个复选框问题到单元中.
#. 选择 **编辑**. 简单编辑器就打开了. 
#. 用你自己的问题文本替代样本问题文本.
#. 确定你想让学生回答的问题的文本描述,用双肩括号括住 (``>>问题<<``).这个问题文本是这个问题的访问标签。
#. 将每个答案选项放在单独的行中。
#. 选择你设置的答案选项, 然后在工具烂选择**复选框**.在每个选项的旁边就出现了一对括号.
#. 为了识别每个正确答案, 要在这个选项旁边的括号中间添加一个**x**.
#. 要提供一个说明, 选择说明文本然后从工具栏中选择**说明**. ``[说明]`` 出现在说明文本的前面和后面。
#. 选择 **设置**并为这个问题提供一个识别 **显示名称**.
#. 为这个问题定义额外的设置. 更多相关信息,请查看： :ref:`Problem Settings`.
#. 选择 **保存**.


For the example problem illustrated above, the following text displays in the
problem component.

::

    Learning about the benefits of preventative healthcare can be particularly 
    difficult. >>Check all of the reasons below why this may be the case.<<

    [x] A large amount of time passes between undertaking a preventative measure and seeing the result. 
    [ ] Non-immunized people will always fall sick. 
    [x] If others are immunized, fewer people will fall sick regardless of a particular individual's choice to get immunized or not. 
    [x] Trust in healthcare professionals and government officials is fragile. 

.. please do not line wrap this text.

    [explanation]
    People who are not immunized against a disease may still not fall sick from the disease. If someone is trying to learn whether or not preventative measures against the disease have any impact, he or she may see these people and conclude, since they have remained healthy despite not being immunized, that immunizations have no effect. Consequently, he or she would tend to believe that immunization (or other preventative measures) have fewer benefits than they actually do.
    [explanation]

========================================================================
Use the Advanced Editor to Edit a Checkbox Problem 
========================================================================

To use the :ref:`Advanced Editor<Advanced Editor>` to edit a checkbox
problem, follow these steps.

#. Follow the steps for creating the problem in the :ref:`Simple Editor<Use
   the Simple Editor to Create a Checkbox Problem>`.
#. Select **Advanced Editor**, and then edit the XML to add the tags and
   attributes you want. An example follows.

.. code-block:: xml

  <problem>
  <p>Learning about the benefits of preventative healthcare can be particularly difficult. Check all of the reasons below why this may be the case.</p>

  <choiceresponse>
    <checkboxgroup label="Check all of the reasons below why this may be the case">
      <choice correct="true"><text>A large amount of time passes between undertaking a preventative measure and seeing the result.</text></choice>
      <choice correct="false"><text>Non-immunized people will always fall sick.</text></choice>
      <choice correct="true"><text>If others are immunized, fewer people will fall sick regardless of a particular individual's choice to get immunized or not.</text></choice>
      <choice correct="true"><text>Trust in healthcare professionals and government officials is fragile.</text></choice>
    </checkboxgroup>
  </choiceresponse>

  <solution>
    <div class="detailed-solution">
      <p>Explanation</p>
      <p>People who are not immunized against a disease may still not fall sick from the disease. If someone is trying to learn whether or not preventative measures against the disease have any impact, he or she may see these people and conclude, since they have remained healthy despite not being immunized, that immunizations have no effect. Consequently, he or she would tend to believe that immunization (or other preventative measures) have fewer benefits than they actually do.</p>
   </div>
  </solution>
  </problem>

.. _Use Feedback in a Checkbox Problem:

********************************************
Use Feedback in a Checkbox Problem
********************************************

You can add feedback in a checkbox problem using the simple editor
or the advanced editor. For an overview of feedback in problems, see
:ref:`Adding Feedback and Hints to a Problem`.

In checkbox problems, you can provide feedback for each option that a learner
can select, with distinct feedback depending on whether or not the learner
selects that option. This means that there are four possible types of feedback.

* The learner selects a correct option. This type of feedback
  should indicate why the option is correct.

* The learner does not select a correct option. This type of feedback should
  indicate that the learner missed checking this option and why it is correct.

* The learner selects an incorrect option. This type of feedback should
  indicate that the learner incorrectly checked this option and why it is
  incorrect

* The learner does not select an incorrect option. This type of feedback should
  reinforce why the learner correctly left this option unselected.

=============================
Compound Feedback
=============================

You can configure the checkbox problem to provide compound feedback.
Compound feedback is feedback given for a specific combination of options. For
example, if you have three possible option in the problem, you can define
specific feedback for when a learner selects each combination of possible
options.

* A
* B
* C
* A, B
* B, C
* A, C
* A, B, C
  
For problems with more than three options, providing specific feedback for each
combination can become difficult. For such problems, you can define compound
feedback for more likely combinations of option or for combinations of option
that reflect common learner misunderstandings. If you do not define feedback
for a combination that a learner selects, the learner receives feedback for the
individual selections.

=======================================
Configure Feedback in the Simple Editor
=======================================

You can configure individual option and compound feedback in the :ref:`Simple
Editor<Simple Editor>`. When you create a new checkbox problem, select the
template **Checkboxes with Hints and Feedback**. This template has example
feedback syntax that you can replace.

Configure Feedback for Individual Options
******************************************

In the simple editor, you configure individual option feedback with the
following syntax.

::

  [x] answer  {{ selected: Feedback when learner selects this option. }, 
  {unselected: Feedback when the learner does not select this option.}}

.. note:: You can use ``S`` for ``selected`` and ``U`` for unselected.

For example, the following problem has feedback for each option.

::

  >>Which of the following is an example of a fruit? Check all that apply.<<

  [x] apple  {{ selected: You are correct that an apple is a fruit because it
  is the fertilized ovary that comes from an apple tree and contains seeds. },
  { unselected: Remember that an apple is also a fruit.}}

  [x] pumpkin {{ selected: You are correct that a pumpkin is a fruit because it
  is the fertilized ovary of a squash plant and contains seeds.}, { unselected:
  Remember that a pumpkin is also a fruit.}}

  [ ] potato   {{ U: You are correct that a potato is a vegetable because it is
  an edible part of a plant in tuber form.}, { S: A potato is a vegetable, not
  a fruit, because it does not come from the flower on a plant or tree and does
  not contain seeds.}}

  [x] tomato  {{ S: You are correct that a tomato is a fruit because it is the
  fertilized ovary of a tomato plant and contains seeds. }, { U: Many people
  mistakenly think a tomato is a vegetable. However, because a tomato is the
  fertilized ovary of a tomato plant and contains seeds it is classified as a
  fruit.}}


Configure Compound Feedback
****************************

In the simple editor, you configure compound feedback after the possible
options, with the following syntax.

::

  {{ ((Answer Combination)) Feedback when learner selects this combination of
  options.}}

For example, the following compound feedback is used when learners select
options **A, B, and D** or **A, B, C, and D**.

::

  {{ ((A B D)) An apple, pumpkin, and tomato are all fruits as they are all the
  fertilized ovaries of a plant and contain seeds. }} 

  {{ ((A B C D)) You are correct that an apple, pumpkin, and tomato are all
  fruits as they are all the fertilized ovaries of a plant and contain seeds.
  However, a potato is not a fruit as it is an edible part of a plant in tuber
  form and is classified as a vegetable.  }}

=========================================
Configure Feedback in the Advanced Editor
=========================================

You can configure individual option and compound feedback in the :ref:`Advanced
Editor<Advanced Editor>`.

Configure Individual Option Feedback
*************************************

In the advanced editor, you configure individual option feedback with the
following syntax.

.. code-block:: xml

    <choice correct="true">Choice label
      <choicehint selected="true">
        Feedback for when learner selects this answer.
      </choicehint>
      <choicehint selected="false">
        Feedback for when learner does not select this answer.
      </choicehint>
    </choice>

For example, the following problem has feedback for each option.

.. code-block:: xml

  <choiceresponse> 
    <checkboxgroup label="Which of the following is an example
    of a fruit? Check all that apply." direction="vertical">
      <choice correct="true">apple
        <choicehint selected="true">You are correct that an apple is a fruit 
          because it is the fertilized ovary that comes from an apple tree and 
          contains seeds.
        </choicehint>
        <choicehint selected="false">Remember that an apple is also a 
          fruit.
        </choicehint>
      </choice>
      <choice correct="true">pumpkin
        <choicehint selected="true">You are correct that a pumpkin is a fruit 
          because it is the fertilized ovary of a squash plant and contains 
          seeds.
        </choicehint>
        <choicehint selected="false">Remember that a pumpkin is also a 
          fruit.
        </choicehint>
      </choice>
      <choice correct="false">potato
        <choicehint selected="true">A potato is a vegetable, not a fruit, 
          because it does not come from the flower on a plant or tree and does 
          not contain seeds.
        </choicehint>
        <choicehint selected="false">You are correct that a potato is 
          classified as a vegetable because it is an edible part of a plant in 
          tuber form.
        </choicehint>
      </choice>
      <choice correct="true">tomato
        <choicehint selected="true">You are correct that a tomato is 
          classified as a fruit because it is the fertilized ovary of a tomato 
          plant and contains seeds.
        </choicehint>
        <choicehint selected="false">Many people mistakenly think a tomato is 
          a vegetable. However, because a tomato is the fertilized ovary of a 
          tomato plant and contains seeds it is classified as a fruit.
        </choicehint>
      </choice>
    </checkboxgroup>
  </choiceresponse>

Configure Compound Feedback
***************************

In the advanced editor, you define compound feedback in the ``<compoundhint>``
element within the ``<checkboxgroup>`` element.

.. code-block:: xml

  <compoundhint value="Answer Combination">
    Feedback when learner selects this combination of answers.
  </compoundhint>}}

For example, the following compound feedback is used when learners select
options **A, B, and D** or **A, B, C, and D**.

.. code-block:: xml

  <compoundhint value="A B D">An apple, pumpkin, and tomato are all fruits as 
    they all are fertilized ovaries of a plant and contain seeds.
  </compoundhint>
  <compoundhint value="A B C D">You are correct that an apple, pumpkin, and 
    tomato are all fruits as they all are fertilized ovaries of a plant and 
    contain seeds. However, a potato is not a fruit as it is an edible part of 
    a plant in tuber form and is classified as a vegetable.
  </compoundhint>

.. _Use Hints in a Checkbox Problem:

********************************************
Use Hints in a Checkbox Problem
********************************************

You can add hints to a checkbox problem, using the simple editor
or the advanced editor. For an overview of hints in problems, see
:ref:`Adding Feedback and Hints to a Problem`.

.. include:: ../../../shared/exercises_tools/Subsection_configure_hints.rst

.. _Checkbox Problem XML:

****************************
Checkbox Problem XML 
****************************

============
Template
============

.. code-block:: xml

  <problem>
  <legend>Question text</legend>
  <choiceresponse>
    <checkboxgroup label="label text">
      <choice correct="false">
        Answer option A (incorrect)
        <choicehint selected="true">
          Feedback for when learner selects this answer.
        </choicehint>
        <choicehint selected="false">
          Feedback for when learner does not select this answer.
        </choicehint>
      </choice>
      <choice correct="true">
        Answer option B (correct)
        <choicehint selected="true">
          Feedback for when learner selects this answer.
        </choicehint>
        <choicehint selected="false">
          Feedback for when learner does not select this answer.
        </choicehint>
      </choice>
      <choice correct="false">
        Answer option C (correct)
        <choicehint selected="true">
          Feedback for when learner selects this answer.
        </choicehint>
        <choicehint selected="false">
          Feedback for when learner does not select this answer.
        </choicehint>
      </choice>
      <compoundhint value="A B">
        Feedback when answers A and B are selected.
      </compoundhint>
     <compoundhint value="A C">
        Feedback when answers A and C are selected.
      </compoundhint>
    </checkboxgroup>
  </choiceresponse>

  <demandhint>
    <hint>Hint 1</hint>
    <hint>Hint 2</hint>
    <hint>Hint 3</hint>
  </demandhint>

  <solution>
    <div class="detailed-solution">
      <p>Solution or Explanation Heading</p>
      <p>Solution or explanation text</p>
     </div>
  </solution>
  </problem>

======
Tags
======

* ``<choiceresponse>`` (required): Specifies that the problem contains options
  for learners to choose from.

* ``<checkboxgroup>`` (required): Specifies that the problem is a checkbox
  problem.

* ``<compoundhint>`` (optional): Specifies feedback for a specific combination
  of answers.

* ``<choice>`` (required): Designates an answer option.
  
* ``<demandhint>`` (optional): Specifies hints for the learner.

**Tag:** ``<choiceresponse>``

Specifies that the problem contains options for learners to choose from.

  Attributes

  (none)

  Children

  ``<checkboxgroup>``

**Tag:** ``<checkboxgroup>``

Specifies that the problem is a checkbox problem.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - label (required)
       - Specifies the name of the response field.

  Children

  ``<choice>``
  ``<compoundhint>`` 

**Tag:** ``<choice>``

Designates an answer option.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - true (at least one required)
       - Indicates a correct answer. For checkbox problems, one or more
         ``<choice>`` tags can contain a correct answer.
     * - false (at least one required)
       - Indicates an incorrect answer.

  Children
  
  ``<choicehint>``

**Tag:** ``<choicehint>``

Specifies a hint for the answer option.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - selected (required)
       - ``true`` or ``false``. Indicates if the hint is given when the answer
         option is selected, or when it is not selected.

  Children
  
  (none)

**Tag:** ``<compoundhint>``

Designates feedback for a specific combination of answers.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - value (at least one required)
       - Indicates which combination of selected answers triggers this
         feedback.

  Children
  
  (none)

**Tag:** ``<demandhint>``

Specifies hints available to the learner.

  Children
  
  ``<hint>``

**Tag:** ``<hint>``

Specifies a hint available to the learner.

  Children
  
  (none)

.. _Using edX Insights: http://edx.readthedocs.org/projects/edx-insights/en/latest/
