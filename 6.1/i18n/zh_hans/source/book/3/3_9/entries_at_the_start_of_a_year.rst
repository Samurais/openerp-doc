.. i18n: .. index::
.. i18n:    single: closing; end of year; opening; opening entry
..

.. index::
   single: closing; end of year; opening; opening entry

.. i18n: Opening and Closing a Financial Year
.. i18n: ====================================
..

会计年度的启用和结账
====================================

.. i18n: At the end of a financial year, you will have to transfer the closing balance of that year as an opening balance to the new financial year. OpenERP allows you to automatically post such an entry. You can transfer the new opening balance numerous times, because it is impossible to close a year at once. Correction entries will have to be made, due to which balances will change. The new balance can easily be transferred through a wizard, so you do not have to keep track of each correction entry made in the previous financial year.
..

在会计年度结束时，您必须将该年度的期末余额结转成新的会计年度的期初余额。 OpenERP允许您自动生成该分录。您可以多次结转期初余额，因为一次就关闭一个会计年度是不可能的。由于余额会变化因此需要相应修改开账分录。新的余额可很容易地通过一个向导结转，因此您不必记住在以前会计年度中的每一次修改。

.. i18n: .. note:: OpenERP Accounting
.. i18n: 
.. i18n:     The procedure below is valid if you already have a financial year with entries in OpenERP.
..

.. note:: OpenERP会计

    以下步骤对您已经在OpenERP中具有一个有会计凭证的会计年度有效。

.. i18n: Steps to Open a New Financial Year in an Existing OpenERP Configuration
.. i18n: -----------------------------------------------------------------------
..

在一个已有的 OpenERP 配置中，逐步启用一个新的会计年度
-----------------------------------------------------------------------

.. i18n: .. index::
.. i18n:    single: accounts; start of year
..

.. index::
   single: accounts; start of year

.. i18n: Before generating the opening balance for your various accounts, you have to go through several steps.
..

在为您的每个科目生成期初余额之前，您需要经过多个步骤。

.. i18n: 1. Create the new Financial Year
..

1. 创建新的会计年度

.. i18n: Create the new financial year as explained in :ref:`financialyear`.
..

创建新的会计年度在 :ref:`financialyear` 中有详细解释。

.. i18n: 2. Define an Opening Period
..

2. 定义一个打开的会计期间

.. i18n: Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Periods --> Periods` and create a new period for the financial year you wish to open (in case it has not been generated automatically). Make sure to link the period to the newly defined financial year. Select the :guilabel:`Opening/Closing Period` checkbox to indicate that this period should be used for opening entries. Both dates typically match the first day of your financial year (e.g. 01/01/YYYY).
..

通过菜单 :menuselection:`Accounting --> Configuration --> Financial Accounting --> Periods --> Periods` 为一个您想打开的会计年度创建新的会计期间 (假设会计期间没有自动生成)。确保会计期间联系上了新定义的会计年度。 选择 :guilabel:`Opening/Closing Period` 选项框标明 该会计期间用于期初分录。两个日期通常和您的会计年度的第一天相同(比如 01/01/YYYY).

.. i18n: 3. Check the Account Types
..

3. 检查科目类型

.. i18n: Before generating the opening entries, make sure to check the defined account types, more specifically the :guilabel:`Deferral Method`.
.. i18n: The deferral method determines whether and how account entries will be transferred to the new financial year. There are four possible deferral methods: None, Balance, Detail, Unreconciled.
..

生成期初分录之前，确认检查过定义的科目类型，具体说是科目的结转方式， :guilabel:`Deferral Method`.
结转方式决定了是否和如何将余额结转到新的会计年度。有四种可能的结转方法：不结转, 余额结转, 明细结转, 未核销部分结转。

.. i18n: =============== ======================================================================
.. i18n: Deferral Method Action
.. i18n: =============== ======================================================================
.. i18n: None            Nothing will be transferred (typically P&L accounts)
.. i18n: Balance         Account balance will be transferred (typically Balance Sheet accounts)
.. i18n: Detail          All entries are transferred, also reconciled entries
.. i18n: Unreconciled    Only entries that are not reconciled on the first day of the new
.. i18n:                 financial year will be transferred (typically receivable and payable)
.. i18n: =============== ======================================================================
..

=============== ======================================================================
结转方式        动作
=============== ======================================================================
None            不结转 (常用于损益类科目)
Balance         仅结转科目余额(通常是有余额的科目)
Detail          所以分录都结转，包括已核销分录
Unreconciled    仅结转在新会计年度第一天核销后余额(典型的如应收应付科目)
=============== ======================================================================

.. i18n: 4. Check the Link between Account and Account Type.
..

4. 检查科目与科目类型之间的联系

.. i18n: Check whether each account is linked to the correct account type to avoid generating an incorrect opening entry.
..

检查是否每个科目都设置成了正确的科目类型以避免生成错误的期初分录。

.. i18n: 5. Create an Opening/Closing Journal
..

5. 创建一个 Opening/Closing Journal

.. i18n: Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
.. i18n: Create a new journal to post your opening entries. Make sure to respect the following settings:
..

通过菜单 :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
创建一个新的分类账来存放期初分录。 请务必遵守以下规则:

.. i18n:     1. :guilabel:`Type` should be :guilabel:`Opening/Closing Situation`.
.. i18n:     2. :guilabel:`Standard debit/credit account` could be something like 140000 Benefits.
.. i18n:     3. :guilabel:`Centralised counterpart` will be checked automatically when select the journal type, to avoid a counterpart on each line, and instead have one debit and one credit entry on the corresponding opening account.
.. i18n:     4. The :guilabel:`Entry Sequence` will also be created automatically on save.
..

    1. :guilabel:`Type` 应为 :guilabel:`Opening/Closing Situation`。
    2. :guilabel:`Standard debit/credit account` 应为类似“140000 Benefits"。
    3. :guilabel:`Centralised counterpart` 当你选择分类账类型时会自动选上，以避免在每一行上有副本，并代替相应的开账科目的一个解放和贷方分录。
    4. 在保存时会自动创建 :guilabel:`Entry Sequence` 。

.. i18n: Generating the Opening Entry
.. i18n: ----------------------------
..

生成期初分录
----------------------------

.. i18n: To automatically generate the opening entries based on your actual books, OpenERP provides a wizard. Go to :menuselection:`Accounting --> Periodical Processing --> End of Period --> Generate Opening Entries`.
..

OpenERP提供了一个向导以根据您实际的帐簿自动生成期初分录。在菜单 :menuselection:`Accounting --> Periodical Processing --> End of Period --> Generate Opening Entries`。

.. i18n: In the wizard, enter the financial year for which you want to transfer the balances (:guilabel:`Fiscal Year to close`). Select the :guilabel:`New Fiscal Year` (the year in which you want to generate the opening entry). You also have to select the journal and the period to post the opening entries. The description for the opening entry is proposed by default, but of course you can enter your own description, such as *Opening Entry for financial year YYYY*. Then you click the :guilabel:`Create` button to generate the opening entry according to the settings defined.
..

在向导中，输入您想结转余额的会计年度 (:guilabel:`Fiscal Year to close`)。 然后选择 :guilabel:`New Fiscal Year` (您要生成期初分录的会计年度)。 您还必须选择提交期初分录的帐簿和会计期间。会生成默认的期初分录摘要，当然您也可以输入您自己的摘要，比如 *"YYYY年期初分录"* 。 最后您点击 :guilabel:`Create` 按钮即可根据您的设置生成期初分录。

.. i18n: To have a look at the draft opening entry that has been generated, go to :menuselection:`Accounting --> Journal Entries --> Journal Entries`. Click the :guilabel:`Unposted` button to filter only draft entries. Open the corresponding entry and verify the data. Click the :guilabel:`Post` button to confirm the entry.
..

要检查自动生成的草稿状态的期初分录，通过菜单 :menuselection:`Accounting --> Journal Entries --> Journal Entries` . 点击 :guilabel:`Unposted` 按钮可过滤出仅草稿状态的分录。打开相应的分录并校验数据。点击 :guilabel:`Post` 按钮确认分录。

.. i18n: .. note:: Changes in Previous Financial Year
.. i18n: 
.. i18n:     As long as the audit is ongoing, extra entries may be added to the financial year to close. To automatically have the correct balances, OpenERP allows you to use the `Cancel Opening Entries` wizard. This wizard will automatically cancel the existing opening entry.
.. i18n: 
.. i18n:     To update the balances to show the correct results, you should run the :guilabel:`Generate Opening Entries:guilabel:` wizard again. The new opening entry will contain the correct balances. This way, you can generate your opening entry as many times as required.
..

.. note:: 上一年度有变化

    只要审计工作还在进行，就有可能在已关闭的会计年度中增加额外的分录。要自动获得正确的余额，OpenERP允许您使用 `Cancel Opening Entries` 向导，这个向导会自动取消已经存在的期初分录。

    要更新余额显示正确的结果，需要您再次运行 :guilabel:`Generate Opening Entries:guilabel:` 向导，新的期初分录将包含正确的余额。这样，您可根据需要多次生成期初分录。

.. i18n: Closing a Financial Year
.. i18n: ------------------------
..

会计年度结账
------------------------

.. i18n: To close a financial year, use the menu :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Fiscal Year`.
.. i18n: A wizard opens asking you for the financial year to close.
..

要关闭一个会计年度，使用菜单 :menuselection:`Accounting--> Periodical Processing --> End of Period --> Close a Fiscal Year`.
一个向导会询问您将关闭的会计年度的信息。

.. i18n: When the year is closed, you can no longer create or modify any transactions in that year.
.. i18n: So you should always make a backup of the database before closing the fiscal year. Closing a year is not mandatory, and you could easily do that sometime in the following year, when your accounts are finally sent to the statutory authorities, and no further modifications are permitted.
..

一旦关闭了一个会计年度，您将不能在该年度中新增或修改任何业务。因此切记务必在关闭会计年度前备份数据库。关闭会计年度并非强制性需要，并且当您的会计报表已经交给法定当局，而且不再做任何修改后，您可以在下一年度中任何时候做这件事情。

.. i18n: .. figure::  images/account_fy_close.png
.. i18n:    :scale: 75
.. i18n:    :align: center
.. i18n: 
.. i18n:    *Closing a Financial Year*
..

.. figure::  images/account_fy_close.png
   :scale: 75
   :align: center

   *关闭会计年度*

.. i18n: Steps to Start your Financial Year
.. i18n: ==================================
..

逐步启动会计年度
==================================

.. i18n: When you decide to do your accounting in OpenERP, and you already have an accounting system, you should enter your opening balance and outstanding entries in OpenERP. Make sure you configure your accounting system as explained in the Configuration chapter.
.. i18n: Below we explain the minimal configuration required to post your opening balance and outstanding entries.
..

When you decide to do your accounting in OpenERP, and you already have an accounting system, you should enter your opening balance and outstanding entries in OpenERP. Make sure you configure your accounting system as explained in the Configuration chapter.
Below we explain the minimal configuration required to post your opening balance and outstanding entries.

.. i18n: 1. Create the new Financial Year
..

1. Create the new Financial Year

.. i18n: Create the new financial year as explained in :ref:`financialyear`.
..

Create the new financial year as explained in :ref:`financialyear`.

.. i18n: 2. Define an Opening Period
..

2. Define an Opening Period

.. i18n: Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Periods --> Periods` and create a new period for the financial year you wish to open (in case it has not been generated automatically). Make sure to link the period to the newly defined financial year. Select the :guilabel:`Opening/Closing Period` checkbox to indicate that this period should be used for opening entries. Both dates typically match the first day of your financial year (e.g. 01/01/YYYY).
..

Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Periods --> Periods` and create a new period for the financial year you wish to open (in case it has not been generated automatically). Make sure to link the period to the newly defined financial year. Select the :guilabel:`Opening/Closing Period` checkbox to indicate that this period should be used for opening entries. Both dates typically match the first day of your financial year (e.g. 01/01/YYYY).

.. i18n: 3. Check the Account Types
..

3. Check the Account Types

.. i18n: Before generating the opening entries, make sure to check the defined account types, more specifically the :guilabel:`Deferral Method`.
.. i18n: The deferral method determines whether and how account entries will be transferred to the new financial year. There are four possible deferral methods: None, Balance, Detail, Unreconciled.
..

Before generating the opening entries, make sure to check the defined account types, more specifically the :guilabel:`Deferral Method`.
The deferral method determines whether and how account entries will be transferred to the new financial year. There are four possible deferral methods: None, Balance, Detail, Unreconciled.

.. i18n: =============== ======================================================================
.. i18n: Deferral Method Action
.. i18n: =============== ======================================================================
.. i18n: None            Nothing will be transferred (typically P&L accounts)
.. i18n: Balance         Account balance will be transferred (typically Balance Sheet accounts)
.. i18n: Detail          All entries are transferred, also reconciled entries
.. i18n: Unreconciled    Only entries that are not reconciled on the first day of the new
.. i18n:                 financial year will be transferred (typically receivable and payable)
.. i18n: =============== ======================================================================
..

=============== ======================================================================
Deferral Method Action
=============== ======================================================================
None            Nothing will be transferred (typically P&L accounts)
Balance         Account balance will be transferred (typically Balance Sheet accounts)
Detail          All entries are transferred, also reconciled entries
Unreconciled    Only entries that are not reconciled on the first day of the new
                financial year will be transferred (typically receivable and payable)
=============== ======================================================================

.. i18n: 4. Define Accounts
..

4. 定义科目表

.. i18n: Check whether each account with an opening balance has been defined in the Chart of Accounts and is linked to the correct account type.
.. i18n: We recommend you to define one or more suspense accounts to post your outstanding entries from the previous financial year. Check the :guilabel:`Reconcile` for such suspense accounts, because their balance will be zero.
..

Check whether each account with an opening balance has been defined in the Chart of Accounts and is linked to the correct account type.
We recommend you to define one or more suspense accounts to post your outstanding entries from the previous financial year. Check the :guilabel:`Reconcile` for such suspense accounts, because their balance will be zero.

.. i18n: 5. Create an Opening/Closing Journal
..

5. Create an Opening/Closing Journal

.. i18n: Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
.. i18n: Create a new journal to post your opening entries. Make sure to respect the following settings:
..

Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
Create a new journal to post your opening entries. Make sure to respect the following settings:

.. i18n:     1. :guilabel:`Type` should be :guilabel:`Opening/Closing Situation`.
.. i18n:     2. :guilabel:`Standard debit/credit account` could be something like 140000 Benefits.
.. i18n:     3. :guilabel:`Centralised counterpart` will be checked automatically when select the journal type, to avoid a counterpart on each line, and instead have one debit and one credit entry on the corresponding opening account.
.. i18n:     4. The :guilabel:`Entry Sequence` will also be created automatically on save.
.. i18n: 
.. i18n: 6. Create a Purchase and/or Sales Journal for Outstanding Entries
..

    1. :guilabel:`Type` should be :guilabel:`Opening/Closing Situation`.
    2. :guilabel:`Standard debit/credit account` could be something like 140000 Benefits.
    3. :guilabel:`Centralised counterpart` will be checked automatically when select the journal type, to avoid a counterpart on each line, and instead have one debit and one credit entry on the corresponding opening account.
    4. The :guilabel:`Entry Sequence` will also be created automatically on save.

6. Create a Purchase and/or Sales Journal for Outstanding Entries

.. i18n: We recommend you to create separate purchase and sales journals to post the outstanding entries from your previous accounting system. This will allow you to easily keep track of your opening entries.
..

We recommend you to create separate purchase and sales journals to post the outstanding entries from your previous accounting system. This will allow you to easily keep track of your opening entries.

.. i18n: Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
.. i18n: Create a new purchase and sales journal to post your outstanding entries. Make sure to respect the following settings:
..

Go to :menuselection:`Accounting --> Configuration --> Financial Accounting --> Journals --> Journals`.
Create a new purchase and sales journal to post your outstanding entries. Make sure to respect the following settings:

.. i18n:     1. :guilabel:`Type` should be :guilabel:`Purchase` or `Sales`.
.. i18n:     2. The :guilabel:`Entry Sequence` will also be created automatically on save.
..

    1. :guilabel:`Type` should be :guilabel:`Purchase` or `Sales`.
    2. The :guilabel:`Entry Sequence` will also be created automatically on save.

.. i18n: Now you can start entering your outstanding customer and supplier entries according to your list of open entries at the end of the year.
..

Now you can start entering your outstanding customer and supplier entries according to your list of open entries at the end of the year.

.. i18n: Go to the menu :menuselection:`Accounting --> Customers --> Customer Invoices` to post your outstanding sales entries. To post your outstanding purchase entries, go to Go to the menu :menuselection:`Accounting --> Suppliers --> Supplier Invoices`.
..

Go to the menu :menuselection:`Accounting --> Customers --> Customer Invoices` to post your outstanding sales entries. To post your outstanding purchase entries, go to Go to the menu :menuselection:`Accounting --> Suppliers --> Supplier Invoices`.

.. i18n: We recommend you to use suspense accounts instead of expense or income accounts. Indeed, your expense and income accounts have already been posted in the previous financial year, and there is no need to transfer these balances. The outstanding entries from previous financial years should not contain any VAT entries; they only get the balance the customer still has to pay you, or the balance you have to pay to the supplier.
..

We recommend you to use suspense accounts instead of expense or income accounts. Indeed, your expense and income accounts have already been posted in the previous financial year, and there is no need to transfer these balances. The outstanding entries from previous financial years should not contain any VAT entries; they only get the balance the customer still has to pay you, or the balance you have to pay to the supplier.

.. i18n: 7. Enter the Opening Balance (Miscellaneous Entry)
..

7. Enter the Opening Balance (Miscellaneous Entry)

.. i18n: For each account that needs to be reopened, enter account data (debit or credit) in the journal. For this operation, go to the menu :menuselection:`Accounting --> Journal Entries --> Journal Entries` and select a miscellaneous journal.
..

For each account that needs to be reopened, enter account data (debit or credit) in the journal. For this operation, go to the menu :menuselection:`Accounting --> Journal Entries --> Journal Entries` and select a miscellaneous journal.

.. i18n: .. tip:: Import
.. i18n: 
.. i18n:     You can also use OpenERP's generic import tool if you load the balance of each of your accounts from other accounting software.
..

.. tip:: Import

    You can also use OpenERP's generic import tool if you load the balance of each of your accounts from other accounting software.

.. i18n: .. Copyright © Open Object Press. All rights reserved.
..

.. Copyright © Open Object Press. All rights reserved.

.. i18n: .. You may take electronic copy of this publication and distribute it if you don't
.. i18n: .. change the content. You can also print a copy to be read by yourself only.
..

.. You may take electronic copy of this publication and distribute it if you don't
.. change the content. You can also print a copy to be read by yourself only.

.. i18n: .. We have contracts with different publishers in different countries to sell and
.. i18n: .. distribute paper or electronic based versions of this book (translated or not)
.. i18n: .. in bookstores. This helps to distribute and promote the OpenERP product. It
.. i18n: .. also helps us to create incentives to pay contributors and authors using author
.. i18n: .. rights of these sales.
..

.. We have contracts with different publishers in different countries to sell and
.. distribute paper or electronic based versions of this book (translated or not)
.. in bookstores. This helps to distribute and promote the OpenERP product. It
.. also helps us to create incentives to pay contributors and authors using author
.. rights of these sales.

.. i18n: .. Due to this, grants to translate, modify or sell this book are strictly
.. i18n: .. forbidden, unless Tiny SPRL (representing Open Object Press) gives you a
.. i18n: .. written authorisation for this.
..

.. Due to this, grants to translate, modify or sell this book are strictly
.. forbidden, unless Tiny SPRL (representing Open Object Press) gives you a
.. written authorisation for this.

.. i18n: .. Many of the designations used by manufacturers and suppliers to distinguish their
.. i18n: .. products are claimed as trademarks. Where those designations appear in this book,
.. i18n: .. and Open Object Press was aware of a trademark claim, the designations have been
.. i18n: .. printed in initial capitals.
..

.. Many of the designations used by manufacturers and suppliers to distinguish their
.. products are claimed as trademarks. Where those designations appear in this book,
.. and Open Object Press was aware of a trademark claim, the designations have been
.. printed in initial capitals.

.. i18n: .. While every precaution has been taken in the preparation of this book, the publisher
.. i18n: .. and the authors assume no responsibility for errors or omissions, or for damages
.. i18n: .. resulting from the use of the information contained herein.
..

.. While every precaution has been taken in the preparation of this book, the publisher
.. and the authors assume no responsibility for errors or omissions, or for damages
.. resulting from the use of the information contained herein.

.. i18n: .. Published by Open Object Press, Grand Rosière, Belgium
..

.. Published by Open Object Press, Grand Rosière, Belgium
