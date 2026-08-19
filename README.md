# Sistemas-ERP-clase
```mermaid
---
config:
  layout: elk
---
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

  %% Flechas verdes: relación base en columna
  Activities --> Customer
  Customer --> Lead
  Lead --> Supplier
  Supplier --> BusinessPartnerMaster

  linkStyle 0,1,2,3 stroke:#22c55e,stroke-width:2px,stroke-linecap:round;

  %% Flechas amarillas: flujo horizontal a la derecha
  Customer --> Opportunity
  Opportunity --> Pricing
  Pricing --> SalesQuotationCRM
  SalesQuotationCRM --> SalesOrder
  SalesOrder --> DeliveryNote
  DeliveryNote --> ARInvoice
  ARInvoice --> IncomingPayments

  linkStyle 4,5,6,7,8,9,10 stroke:#facc15,stroke-width:2px,stroke-linecap:round;

  Lead --> Opportunity
  PurchaseRequest --> PurchaseQuotation
  PurchaseQuotation --> PurchaseOrder
  SalesOrder --- PurchaseOrder
  PurchaseOrder --> GoodsReceiptPO
  GoodsReceiptPO --> APInvoice
  APInvoice --> OutgoingPayments
  APInvoice -.-> APAR

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

