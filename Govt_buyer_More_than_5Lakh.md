```mermaid
graph TD
    subgraph TITLE
        A_title[Dronemart Portal: Govt User Procuremnt For Order Price More Than 5 Lakh]
    end

  

    A[Govt User selects Vendor & Places Order] --> B{Confirmation Pending from Vendor};
    B -- Govt User --> C[Govt User Status: Order Placed, Pending Vendor Confirmation];
    B -- HoD --> D[HoD Status: Awaiting Vendor Confirmation];
    B -- Vendor --> E[Vendor Status: New Order, Awaiting Action];

    E --> F{Vendor Confirms Availability};
    F -- Accepted --> K;
    F -- Rejected (Negotiate) --> NG_AVAIL1{Negotiation Round 1 Availability};

    NG_AVAIL1 -- HoD & Vendor Negotiate --> F;
    NG_AVAIL1 -- Failed Negotiation 1 --> NG_AVAIL2{Negotiation Round 2 Availability};

    NG_AVAIL2 -- HoD & Vendor Negotiate --> F;
    NG_AVAIL2 -- Failed Negotiation 2 --> NG_AVAIL3{Negotiation Round 3 Availability};

    NG_AVAIL3 -- HoD & Vendor Negotiate --> F;
    NG_AVAIL3 -- Failed Negotiation 3 --> H[Vendor Status: Rejected Order];


    H --> I[Govt User Status: Vendor Rejected Order];
    H --> J[HoD Status: Vendor Rejected Order];

    K{Confirmation Pending from HoD};
    K -- Govt User --> L[Govt User Status: Vendor Approved, Waiting for HoD Approval];
    K -- HoD --> M[HoD Status: Action Required - Approve/Reject Vendor];
    K -- Vendor --> N[Vendor Status: Accepted, Waiting for HoD Approval];

    M -- HoD Approves --> O[HoD Status: Approved];
    O --> P{Govt User Generates Work Order};
    P -- Govt User --> Q[Govt User Status: Work Order Generated, Pending HoD Approval];
    P -- HoD --> R[HoD Status: Awaiting Work Order Approval];
    P -- Vendor --> S[Vendor Status: Work Order Generated, Awaiting HoD Approval];

    R -- HoD Approves Work Order --> T[HoD Status: Review pending from Vendor];
    T --> U[Govt User Status: Work Order Approved by HoD, review pending from Vendor];
    T --> V[Vendor Status: Review Work Order];
    T --> W[HoD Status: Review pending from Vendor];

    V --> X{Vendor reviews Work Order};
    X -- Vendor Accepts --> Y[Vendor Status: Work Order Accepted by Vendor, Vendor's Work In-Progress];
    Y -- Govt User --> Z[Govt User Status: Work Order Accepted by Vendor, Vendor's Work In-Progress];
    Y -- HoD --> AA[HoD Status: Work Order Accepted by Vendor, Vendor's Work In-Progress];

    X -- Vendor Rejects --> AB[Vendor Status: Work Order Rejected by Vendor];
    AB --> AC[Govt User Status: Work Order Rejected by Vendor];
    AB --> AD[HoD Status: Work Order Rejected by Vendor];
