# Sistemas-ERP-clase
flowchart LR
Activities((Activities))
Customer((Customer))
Lead((Lead))
Supplier((Supplier))
BusinessPartnerMaster((Business Partner Master))
Opportunity((Opportunity))
Pricing((Pricing))
SalesQuotationCRM((Sales Quotation))
CustomerEquipmentCard((Customer Equipment Card))

ServiceCall((Service Call))
ServiceContract((Service Contract))
ServiceBilling((Service Billing))

ItemMaster((Item Master))
WarehouseManagement((Warehouse Management))

SalesOrder((Sales Order))
DeliveryNote((Delivery Note))
ARInvoice((AR Invoice))
IncomingPayments((Incoming Payments))

PurchaseRequest((Purchase Request))
PurchaseQuotation((Purchase Quotation))
PurchaseOrder((Purchase Order))
GoodsReceiptPO((Goods Receipt PO))
APInvoice((AP Invoice))
OutgoingPayments((Outgoing Payments))

Sourcing((Sourcing))
ProductionOrder((Production Order))
IssueToProduction((Issue to Production))
ReceiptFromProduction((Receipt from Production))
ProductReporting((Product Reporting))
MaterialRequirementsPlanning((Material Requirements Planning))
BillOfMaterials((Bill of Materials))

DemandPlanning((Demand Planning))
BackorderReporting((Backorder Reporting))
InventoryAuditReport((Inventory Audit Report))
AccountBalancesReport((Account Balances Report))

ChartOfAccounts((Chart of Accounts))
GeneralLedgerAccounts((General Ledger Accounts))
GLAccountDetermination((G/L Account Determination))
CostAccounting((Cost Accounting))
JournalEntries((Journal Entries))
FinancialPostings((Financial Postings))

APAR((AP / AR))
CashManagement((Cash Management))
Reconciliation((Reconciliation))
FinancialReporting((Financial Reporting))

Activities --- Customer
Customer --- Lead
Lead --- Supplier
Supplier --- BusinessPartnerMaster

Customer -.-> Opportunity
Opportunity -.-> Pricing
Pricing -.-> SalesQuotationCRM
SalesQuotationCRM -.-> CustomerEquipmentCard
Supplier -.-> CustomerEquipmentCard

CustomerEquipmentCard -.-> ServiceCall
ServiceCall -.-> ServiceContract
ServiceContract -.-> ServiceBilling
ServiceBilling -.-> FinancialPostings

CustomerEquipmentCard --> ItemMaster
ItemMaster --> WarehouseManagement
ItemMaster --> SalesOrder

Customer --> SalesOrder
SalesOrder --> DeliveryNote
DeliveryNote --> ARInvoice
ARInvoice --> IncomingPayments
ARInvoice -.-> APAR

Lead --> PurchaseRequest
PurchaseRequest --> PurchaseQuotation
PurchaseQuotation --> PurchaseOrder
SalesOrder --- PurchaseOrder
PurchaseOrder --> GoodsReceiptPO
GoodsReceiptPO --> APInvoice
APInvoice --> OutgoingPayments
APInvoice -.-> APAR

Supplier --> Sourcing
Sourcing --> ProductionOrder
PurchaseOrder --- ProductionOrder
ProductionOrder --> IssueToProduction
IssueToProduction --> ReceiptFromProduction
ReceiptFromProduction --> ProductReporting

Sourcing --> MaterialRequirementsPlanning
MaterialRequirementsPlanning --> DemandPlanning
ProductionOrder -.-> DemandPlanning
DemandPlanning -.-> BackorderReporting

BillOfMaterials -.-> ChartOfAccounts
ChartOfAccounts --- GeneralLedgerAccounts
GeneralLedgerAccounts --- GLAccountDetermination
GLAccountDetermination --- CostAccounting
CostAccounting --> JournalEntries
JournalEntries --> FinancialPostings
JournalEntries --> InventoryAuditReport
InventoryAuditReport --> AccountBalancesReport
AccountBalancesReport --> FinancialReporting

APAR --> CashManagement
CashManagement --> Reconciliation
Reconciliation --> FinancialReporting
FinancialReporting --> ProductReporting

classDef crm fill:#c8e6c9,stroke:#4caf50,stroke-width:2px,color:#0d2b0f;
classDef service fill:#fff9c4,stroke:#f5e642,stroke-width:2px,color:#4d4300;
classDef sales fill:#ffe0b2,stroke:#ff9800,stroke-width:2px,color:#4d2c00;
classDef inventory fill:#e0e0e0,stroke:#9e9e9e,stroke-width:2px,color:#242424;
classDef purchasing fill:#bbdefb,stroke:#2196f3,stroke-width:2px,color:#062a4d;
classDef finance fill:#ffcdd2,stroke:#f44336,stroke-width:2px,color:#4d0f0a;
classDef production fill:#d1c4e9,stroke:#4a148c,stroke-width:2px,color:#2a0a4d;
classDef reporting fill:#f3e5f5,stroke:#ce93d8,stroke-width:2px,color:#3a1245;

class Activities,Customer,Lead,Supplier,BusinessPartnerMaster,Opportunity,Pricing,SalesQuotationCRM,CustomerEquipmentCard crm
class ServiceCall,ServiceContract,ServiceBilling service
class SalesOrder,DeliveryNote,ARInvoice,IncomingPayments sales
class ItemMaster,WarehouseManagement inventory
class PurchaseRequest,PurchaseQuotation,PurchaseOrder,GoodsReceiptPO,APInvoice,OutgoingPayments purchasing
class FinancialPostings,JournalEntries,APAR,CashManagement,Reconciliation,FinancialReporting,CostAccounting,ChartOfAccounts,GeneralLedgerAccounts,GLAccountDetermination finance
class Sourcing,ProductionOrder,IssueToProduction,ReceiptFromProduction,ProductReporting,MaterialRequirementsPlanning,BillOfMaterials production
class DemandPlanning,BackorderReporting,InventoryAuditReport,AccountBalancesReport reporting