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

  %% Flechas azules: flujo de compras
  PurchaseRequest --> PurchaseQuotation
  PurchaseQuotation --> PurchaseOrder
  PurchaseOrder --> GoodsReceiptPO
  GoodsReceiptPO --> APInvoice
  APInvoice --> OutgoingPayments

  linkStyle 11,12,13,14,15 stroke:#3b82f6,stroke-width:2px,stroke-linecap:round;

  %% Flechas moradas: flujo de producción e inventario
  BillOfMaterials --> MaterialRequirementsPlanning
  MaterialRequirementsPlanning --> Sourcing
  Sourcing --> ProductionOrder
  ProductionOrder --> IssueToProduction
  IssueToProduction --> ReceiptFromProduction
  ReceiptFromProduction --> ProductReporting

  linkStyle 16,17,18,19,20,21 stroke:#4c1d95,stroke-width:2px,stroke-linecap:round;

  %% Flechas rojas: flujo financiero y contable
  ChartOfAccounts --> GeneralLedgerAccounts
  GeneralLedgerAccounts --> GLAccountDetermination
  GLAccountDetermination --> CostAccounting
  CostAccounting --> JournalEntries
  JournalEntries --> ReceiptFromProduction
  ReceiptFromProduction ---> APInvoice
  APInvoice --> APAR
  APAR --> CashManagement
  CashManagement --> Reconciliation
  Reconciliation --> FinancialReporting
  ReceiptFromProduction --> ProductReporting

  linkStyle 22,23,24,25,26,27,28,29,30,31 stroke:#dc2626,stroke-width:2px,stroke-linecap:round;

  %% Flechas rosadas: reportes operativos y financieros
  DemandPlanning --> BackorderReporting
  BackorderReporting --> InventoryAuditReport
  InventoryAuditReport --> AccountBalancesReport
  AccountBalancesReport --> ProductReporting
  ProductReporting --> FinancialReporting

  linkStyle 32,33,34,35,36 stroke:#ec4899,stroke-width:2px,stroke-linecap:round;



