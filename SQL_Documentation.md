# SQL 
### Select
### Update
### Delete
### Insert
### Where
### Create Database,Create table,Distinct,Group by,Order by
### AND,OR,NOT,NULL,Select Top,Min,Max,Count,Avg,Sum,Like
### In,Between
```
Select * from Demodata.pro.tblpurchaseorderheader where strPurchaseOrderNo='PO-BCCL-APR22-6'

select * from Demodata.wms.tblInventoryTransactionHeader where intReferenceId=109204 and intTransactionTypeId=1

select * from Demodata.fin.tblBillRegister where intBillRegisterId=34827

select * from Demodata.inv.tblSupplierInvoiceHeader where intBillId=34827

select * from Demodata.fin.tblPaymentRequest where intPaymentRequestId=34835

select * from Demodata.fin.tblBankJournalHeader where intBankJournalId=290883

//which type of PO to find//

Select * From Demodata.pro.tblPurchaseOrderType where intPurchaseOrderTypeId= 5
```
---
#join query
```
Select H.strAdjustmentJournalCode, H.intAccountId, H.intTransactionId,
 R.intAdjustmentJournalId, R.intGeneralLedgerId, R.strGeneralLedgerName

From  fin.tblAdjustmentJournalHeader H JOIN fin.tblAdjustmentJournalRow R 

ON H.intAdjustmentJournalId = R.intRowId

where H.intBusinessUnitId IN (4)
ORDER BY  R.intGeneralLedgerId;

SELECT * FROM Demodata .dbo.BonusACCL
WHERE EmployeeID=473653

SELECT strBusinessUnitName, intAccountId FROM Demodata.dco.tblBusinessUnit;
```
---
 //Procurement Process//
```
Select * From Demodata.pro.tblPurchaseOrderHeader Where strPurchaseOrderNo = 'PO-ACCL-FEB22-10'

Select * From Demodata.wms.tblInventoryTransactionHeader where intReferenceId = '106433'
And intTransactionTypeId =1

Select * From Demodata.fin.tblBillRegister where intBillRegisterId='29155'

Select * From Demodata.inv.tblSupplierInvoiceHeader where intBillId='29155'

Select * From Demodata.fin.tblPaymentRequest where intPaymentRequestId='28866'

Select * From Demodata.fin.tblBankJournalHeader where  intBankJournalId='268662'

Select * From Demodata.fin.tblAccountingJournal where intAccountingJournalId = 268662
```
---
```
Select * From Demodata.pro.tblPurchaseOrderHeader Where strPurchaseOrderNo = 'PO-ACCL-FEB22-10'

Select * From Demodata.pro.tblPurchaseOrderRow where intPurchaseOrderId=106433

Select * From Demodata.dco.tblUser where intUserId=396377

Select * From Demodata.wms.tblInventoryTransactionHeader where intReferenceId = '106433'
And intTransactionTypeId =1

Select * From Demodata.fin.tblBillRegister where intBillRegisterId='29155'

Select * From Demodata.inv.tblSupplierInvoiceHeader where intBillId='29155'

Select * From Demodata.fin.tblPaymentRequest where intPaymentRequestId='28866'

Select * From Demodata.fin.tblBankJournalHeader where  intBankJournalId='268662'

Select * From Demodata.fin.tblAccountingJournal where intAccountingJournalId = 268662

Select * From Demodata.prt.tblBusinessPartnerBankInformation Where intBusinessPartnerId= 53860

Select * From Demodata.fin.tblBankBranch where intBankId=23 And intBankBranchId = 2891


```
---
###join query
```
Select H.strInventoryTransactionCode, H.dteTransactionDate, H.TransactionGroupId, H.TransactionGroupName,
H.intTransactionTypeId,H.strTransactionTypeName, H.intReferenceTypeId, H.strReferenceTypeName,
H.intReferenceId, H.strReferenceCode, H.intAccountId, H.strAccountName, H.intBusinessUnitId, H.strBusinessUnitName,
H.intSBUId, H.strSBUName, H.intPlantId, H.strPlantName, H.intPurchaseOrgId, 
H.strPurchaseOrgName, H.intWarehouseId, H.dteTransactionDate,  H.dteLastActionDateTime,

R.dteLastActionDateTime, R.intInventoryTransactionId, R.strInventoryTransactionCode, R.intItemId, R.strItemName, R.intUoMId,
R.strUoMName, R.numTransactionQuantity, R.monTransactionValue, R.intInventoryLocationId, R.strInventoryLocationName,
R.intBatchId, R.strBatchNumber, R.intInventoryStockTypeId, R.strInventoryStockTypeName

FROM Demodata.wms.tblInventoryTransactionHeader H Join Demodata.wms.tblInventoryTransactionRow R 
ON H.intInventoryTransactionId = R.intInventoryTransactionId

AND H.dteLastActionDateTime = R.dteLastActionDateTime

Where  R.dteLastActionDateTime BETWEEN  '2021-05-01' AND'2021-05-31' ORDER BY R.dteLastActionDateTime

```
```
Select strBankAccountTypeName, MAX(strBankAccountNo)
From Demodata.fin.tblBankAccount
Group By strBankAccountTypeName
```
```
Select R.intItemId, R.strItemName, R.intUoMId
From Demodata.pro.tblPurchaseOrderHeader H Join Demodata.pro.tblPurchaseOrderRow R
ON  H.intPurchaseOrderId = R.intPurchaseOrderId
```
---
```
SELECT ph.strWarehouseName, pr.intItemId, pr.strItemName, pr.intUoMId, ph.intBusinessUnitId, ph.intWarehouseId,
br.dteBillRegisterDate, ph.dtePurchaseOrderDate, ih.dteTransactionDate, ph.strPurchaseOrderNo

FROM Demodata.pro.tblPurchaseOrderHeader ph join Demodata.pro.tblPurchaseOrderRow pr

on ph.intPurchaseOrderId = pr.intPurchaseOrderId 

join Demodata.wms.tblInventoryTransactionHeader ih 

on pr.intPurchaseOrderId = ih.intReferenceId

join Demodata.fin.tblBillRegister br

ON pr.intPurchaseOrderId = br.intBillRegisterId

where ph.intBusinessUnitId In (4) and ph.intWarehouseId in (142)
```
---
```
SELECT ph.strPurchaseOrderNo, ih.strInventoryTransactionCode,   ph.strWarehouseName, 
 ph.intBusinessUnitId, ph.strBusinessPartnerName, ph.dtePurchaseOrderDate,
ih.dteTransactionDate

FROM Demodata.pro.tblPurchaseOrderHeader ph 
left join Demodata.wms.tblInventoryTransactionHeader ih on ph.intPurchaseOrderId = ih.intReferenceId 
where ph.intBusinessUnitId In (4) and ph.intWarehouseId in (142)
```
---
```
SELECT ph.strPurchaseOrderNo, ih.strInventoryTransactionCode, br.strBillRegisterCode,  ph.strWarehouseName, pr.intItemId,
pr.strItemName, pr.strUoMName, ph.intBusinessUnitId, ph.strBusinessPartnerName, br.dteBillRegisterDate, ph.dtePurchaseOrderDate,
ih.dteTransactionDate, ih.numTotalAmount

FROM Demodata.pro.tblPurchaseOrderHeader ph 
join Demodata.pro.tblPurchaseOrderRow pr on ph.intPurchaseOrderId = pr.intPurchaseOrderId 
left join Demodata.wms.tblInventoryTransactionHeader ih on ph.intPurchaseOrderId = ih.intReferenceId 
left join Demodata.fin.tblBillRegister br ON ih.intBillId = br.intBillRegisterId
join Demodata.wms.tblInventoryTransactionRow tr On  tr.intInventoryTransactionId = ih.intInventoryTransactionId

where ph.intBusinessUnitId In (4) and ph.intWarehouseId in (142) and ih.intTransactionTypeId=1
```
---
```
Select top (200) BP.strBusinessPartnerName 
From Demodata.prt.tblBusinessPartner BP
```
---
```
Select TI.intItemId, TI.strItemCode, TI.strItemName, Ih.strSupplierInvoiceCode, IH.intSupplierInvoiceId
From Demodata.inv.tblSupplierInvoiceHeader IH
Join Demodata.itm.tblItem TI ON IH.intBusinessUnitId = TI.intBusinesUnitId 
```
---
```
//Bank Branch ADD- Routing No//
Select * from Demodata.fin.tblBankBranch where strBankName='SOUTHEAST BANK LTD' and strBankBranchName='CHUADANGA BRANCH'

Select * from Demodata.fin.tblBankBranch where strRoutingNo = '125490108' 

Select * From Demodata.hcm.tblEmployeeBasicInfo where intEmployeeId=514669

select  strUnit, monGrossSalary, monTotalAllowance, monTotalDeduction, monNetPayableSalary, monCanteenBill, 
monPFAmount from Demodata.hcm.tblMonthlySalaryGenerateFull 
```
---
```
Select * From Demodata.hcm.tblEmployeeBasicInfo where intEmployeeId=57933

```
---
```
Select * From Demodata.hcm.tblLeaveApplication where intEmployeeId=57933 and 
dteAppliedFromDate Between  '2022-06-06' and  '2022-06-15'
```
---
```
Select  intUserId, strUserName
From Demodata.dco.tblUser Where intDefaultBusinessUnit = 186
```
---
```
Select PH.intPurchaseOrderId, PH.strPurchaseOrderNo,PH.intBusinessUnitId,PH.strOtherTerms

From Demodata.pro.tblPurchaseOrderHeader PH 
JOIN Demodata.pro.tblPurchaseOrderRow PR ON PH.intPurchaseOrderId = PR.intPurchaseOrderId

Where PH.numReceiveQty is NULL AND PR.intCostCenterId = 0  AND PH.intBusinessUnitId
in (4,8,94, 136,144,171,175,178,180,181,182,183,186,188,189)
and PH.intAccountId = 1 and PH.isActive=1 AND PR.isActive = 1 AND PH.isClosed=0
AND PH.dtePurchaseOrderDate BETWEEN '2022-01-01' AND '2022-06-26'
```
---
```
Select * From Demodata.itm.tblItem where intBusinesUnitId=4 AND isActive=1

```
---
```
 Select * From Demodata.pro.tblPurchaseOrderRow where  intPurchaseOrderId = 106759

 Select * From Demodata.pro.tblPurchaseOrderHeader where strPurchaseOrderNo  = 'PO-ACCL-FEB22-144'

 Select * From Demodata.dco.tblUser where strLoginId LIKE '%sadiaNadira%'   --'%monsurul.accl%'

 Select * From Demodata.fin.tblAdjustmentJournalHeader where strAdjustmentJournalCode = 'JV-ACCl-APR22-5925'
 
 Select * From Demodata.fin.tblAdjustmentJournalRow where intAdjustmentJournalId in (445590 ,445591)
 
 Select * From Demodata.wms.tblInventoryTransactionHeader where intInventoryTransactionId = 34341

 Select * From Demodata.fin.tblBillRegister where intBillRegisterId = 34341

```
---
```
select * from Demodata.cco.tblCostElement where isActive = 1 and intBusinessUnitId
in (4,8,94,136,144,171,175,178,180,181,182,183,186,188,189) 
and intBusinessTransactionId = 0

select * from Demodata.fin.tblBusinessTransaction where isActive=1
and intBusinessUnitId in (186) AND intGeneralLedgerId = 93

Select * from Demodata.fin.tblBusinessTransaction where intBusinessTransactionId in (
Select intBusinessTransactionId From Demodata.cco.tblCostElement where strCostElementName like '%Power and Fuel%')

```
---
```
Select intBusinessUnitId, strBusinessUnitName
From Demodata.dco.tblBusinessUnit Where intAccountId = 1 AND isActive=1 

Select intDepartmentId, strDepartmentName
From Demodata.hcm.tblEmployeeDepartment Where intAccountId = 1  And isActive = 1

Select intDesignationId, strDesignationName
From Demodata.hcm.tblEmployeeDesignation Where intAccountId = 1  And isActive = 1

Select intEmployeeId, intERPEmployeeId, strEmployeeFullName
From Demodata.hcm.tblEmployeeBasicInfo Where intAccountId = 1 AND isActive = 1 AND intEmploymentStatusId=1 
AND intBusinessunitId In (4,8,12,17,94,102,117,136,138,144,171,175,178,
180,181,182,183,184,186,188,189,208,209,210,211,212,213,214,216)

```
---
```
//Controlling Unit (cco) ControllingUnit, costCenter, CostElement//
Select * From Demodata.pro.tblPurchaseOrderHeader Where strPurchaseOrderNo = 'PO-ASLL-JUN22-190'

Select * From Demodata.pro.tblPurchaseOrderRow Where intPurchaseOrderId = 115072

Select * From Demodata.cco.tblControllingUnit where intBusinessUnitid in (17)

Select * from Demodata.cco.tblCostCenter where intBusinessUnitId in (17)

Select * From Demodata.cco.tblCostElement where intBusinessUnitId in (17)
```
---
```
Select * From Demodata.wms.tblItemRequestHeader where strItemRequestCode = 'IR-AEL-JUN22-16'

Select * From Demodata.wms.tblItemRequestRow Where intItemRequestId = 172963

Select sum(numTransactionQuantity) From Demodata.wms.tblInventoryTransactionRow where intItemId in (98185)

Select * From Demodata.wms.tblItemPlantWarehouse where intItemId = 98185

Select * From Demodata.wms.tblItemWarehouseCost where intItemId = 98185
```
---
```
Select  EI.intEmployeeId, EP.strEmployeeFullName, EP.strWorkplaceGroupName, EP.strWorkplaceName,
EP.strBusinessUnitName, EI.strEducationLevel , EI.strDegree, EI.strInstitute, EI.intPassingYear,
EI.strResult, EI.[intMarks(%)], EI.intCGPA

From Demodata.hcm.tblEmployeeEducationInfo EI
JOIN Demodata.hcm.qryEmployeeProfileAll  EP
ON EI.intEmployeeId = EP.intEmployeeId
Where EI.isActive = 1 And EP.isActive = 1 AND EP.intEmploymentStatusId = 1 
AND EP.intBusinessunitId in (Select BusinessunitId from Demodata.[hcm].[funOnboardedBusinessUnit] (1))

```
---
```
//Find MRP PO//
 Select * From Demodata.pro.tblPurchaseOrderHeader  where strPurchaseOrderNo In
 ('PO-ASLL-1-MAY22-109','PO-ASLL-MAY22-78','PO-ASLL-1-MAY22-39','PO-ASLL-1-MAY22-131') 

 Select * From Demodata.pro.tblPurchaseOrderRow Where intPurchaseOrderId In (112004,111493,112003,112599)
 AND intReferenceId = 0

 select * from Demodata.wms.tblInventoryTransactionHeader where intReferenceId In  (112004,111493,112003,112599)
 and intTransactionTypeId=1

 select * from Demodata.fin.tblBillRegister where intBillRegisterId IN (40549,40550,40551,NULL)

 select * from Demodata.inv.tblSupplierInvoiceHeader where intBillId = 40551

 select * from Demodata.fin.tblPaymentRequest where intPaymentRequestId = 0

 select * from Demodata.fin.tblBankJournalHeader where intBankJournalId = 0
```
---
```
Select * From Demodata.dco.tblUser where  intUserReferenceId = 558149

Select * From Demodata.hcm.tblEmployeeBasicInfo where intERPEmployeeId = 523299 

```
---
```
Select * From Demodata.dco.tblBusinessUnit where intBusinessUnitId in (212,209)

Select * From Demodata.fin.tblBusinessUnitGeneralLedger where intBusinessUnitId IN (209,212)

Select * From Demodata.fin.tblBusinessTransaction where intBusinessUnitId = 209

Select * From Demodata.fin.tblBusinessTransaction where intBusinessUnitId = 216

Select * From Demodata.fin.tblAutoJournalGlConfig where intUnitId = 209

Select * From Demodata.fin.tblAutoJournalGlConfig where intUnitId = 216

Select * From Demodata.fin.tblAccountingConfig where intBusinessUnitId = 216

Select * From Demodata.fin.tblBusinessTransaction where intBusinessUnitId = 178 and isActive = 1

Select * From Demodata.dco.tblThirdLabelMenu Where strLabel  LIKE '%loan%'

Select * From Demodata.dco.tblModuleFeature Where intThirdLabelId IN (592,598)

Select * From Demodata.dco.tblModuleFeature Where intThirdLabelId = 598
```
---
```
Select * From Demodata.itm.tblItem Where strItemCode = '177131837'

Select * From Demodata.wms.tblItemPlantWarehouse Where intItemId = 51799 And intPlantId = 81
```
---
```
Select * From Demodata.pro.tblPurchaseOrderHeader Where strPurchaseOrderNo = 'PO-ARMCL-JUL22-48' 

Select * From Demodata.pro.tblPurchaseOrderRow Where intPurchaseOrderId = 116600

select * from Demodata.cco.tblCostCenter where intBusinessUnitId=17 and isActive=1
select * from Demodata.cco.tblCostElement where intBusinessUnitId=17 and isActive=1
select * from Demodata.cco.tblControllingUnit where intBusinessUnitId=17 and isActive=1
```
---
```
Select PH.strPurchaseOrderNo, PH.intPurchaseOrderId,IH.intReferenceId, IH.intBillId,BR.intBillRegisterId, BR.intPaymentRequestId
From Demodata.pro.tblPurchaseOrderHeader PH 
JOIN Demodata.pro.tblPurchaseOrderRow PR ON PH.intPurchaseOrderId = PR.intPurchaseOrderId
JOIN Demodata.wms.tblInventoryTransactionHeader IH On PR.intPurchaseOrderId = IH.intReferenceId AND IH.intTransactionTypeID=1
JOIN Demodata.fin.tblBillRegister BR ON IH.intBillId = BR.intBillRegisterId
JOIN Demodata.fin.tblPaymentRequest P ON  BR.intPaymentRequestId = p.intPaymentRequestId 
JOIN Demodata.fin.tblAccountingJournal AJ On P.intJournalId   = AJ.intAccountingJournalId

Where PR.intPurchaseOrderId = 116345
```
---
```
Select Distinct strItemName  From Demodata.itm.tblItem Order BY strItemName ASC
```
---
```
//Bin Num Updating for get Item Code]
Select * From Demodata.itm.tblItem Where strItemCode =  '110101912'
Select * From Demodata.wms.tblItemPlantWarehouse Where intItemId = 96258
```
---
```
//PR-Purchase Request process//
Select  * From Demodata.pro.tblPurchaseRequestHeader  Where strPurchaseRequestCode = 'PR-ACCL-JUL22-185'

Select * From Demodata.pro.tblPurchaseRequestRow Where intPurchaseRequestId = 48345

Select * From Demodata.pro.tblPurchaseOrderRow where strReferenceCode = 'PR-ACCL-JUL22-185'

Select * From Demodata.pro.tblPurchaseOrderRow Where intReferenceId = 48345
```
---
```
//RoutingNo used Bank Branch Find out//
Select * From Demodata.fin.tblBankBranch where strRoutingNo = '085261514'
```
---
```
//Warehouse Name,ID Plant Id,Name//
Select  * From Demodata.itm.tblItem Where intBusinesUnitId = 188 and isactive = 1  

Select * From Demodata.wms.tblPlantWarehouse Where intBusinessUnitId = 188 and isActive = 1
Select * From Demodata.wms.tblInventoryLocation Where intBusinessUnitId = 188 and isActive = 1

Select * From Demodata.wms.tblItemPlantWarehouse where intBusinessUnitId = 188 And isActive = 1
```
---
```
//PO- is it receive or not//

Select * FRom Demodata.pro.tblPurchaseOrderHeader Where strPurchaseOrderNo = 'PO-MSIL-JUN22-133'     

Select * From Demodata.pro.tblPurchaseOrderRow Where intPurchaseOrderId = 113867   
                
Select * From Demodata.pro.tblPurchaseOrderType Where intPurchaseOrderTypeId = 1

Select * From Demodata.dco.tblBusinessUnit Where intBusinessUnitId = 171
