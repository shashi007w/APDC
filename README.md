```mermaid
graph TD
    subgraph Buyer/Govt User Journey
        A[Access Portal] --> B{Existing User?};
        B -- Yes --> C[Buyer Login];
        B -- No --> D[Buyer Registration - Govt Dept];
        D --> E{Account Verification - if app};
        E --> BuyerDashboard;
        C --> BuyerDashboard;

        subgraph Buyer Dashboard
            BuyerDashboard --> BD1[Search/Browse Vendors];
            BD1 --> BD1a(Filter: Category);
            BD1 --> BD1b(Filter: Location);
            BD1 --> BD1c(Filter: Experience/Ratings);
            BD1 --> BD1d(Filter: Capabilities/Equipment);
            BD1a & BD1b & BD1c & BD1d --> BD1e[View Profiles & Portfolios];
            BD1e --> BD1f{Shortlist?};
            BD1f -- Yes --> BD2[Initiate RFP/Tender];
            BD1f -- No --> BD1;

            BuyerDashboard --> BD2;
            BD2 --> BD2a[Specify Project Requirements];
            BD2a --> BD2b{Order Value?};
            BD2b -- "< Rs.25,000" --> BD2c[Direct Online Purchase];
            BD2c --> BD5a[Meet Specs & Delivery?];
            BD2b -- "Rs.25,000 - Rs.5 Lakhs" --> BD2d[Compare Offers - Min 3 OEMs-Providers];
            BD2b -- "More than Rs.5 Lakhs" --> BD2e[Customization of Orders];

            BD2d --> BD3[Submit RFP];
            BD2e --> BD3[Submit Bid Invitation - Notification sent to Vendors];

            BD3 --> BD4[Receive Quotations/Bids];
            BD4 --> BD5{Evaluate Offers?};
            BD5 -- "Rs.25,000 - Rs.5 Lakhs" --> BD5b[Compare Price - L1 Selection];
            BD5b -- L1 Selected --> BD6;
            BD5b -- No Suitable Offer --> BD7;
            BD5 -- "More than Rs.5 Lakhs" --> BD5c[Financial Bid Evaluation];
            BD5c -- Best Value Identified --> BD6;
            BD5c -- No Suitable Bid --> BD7;

            BD5a -- Yes --> BD6[Admin - APDC Approval];
            BD5a -- No --> BD7[Reject];

            BD6 --> BD8[Work Order Generation];
            BD8 --> BD9[Manage work Order & Communication];
            BD9 --> BD9a(Track Progress & Milestones);
            BD9 --> BD9b(Communicate via Platform);
            BD9 --> BD9c(Share Documents);
            BD9 --> BD10[Work Complete];
            BD10 --> BD11[Rate & Review Vendor];
            BD11 --> BuyerDashboard;
            BD7 --> BuyerDashboard;

            BuyerDashboard --> BD12[View Order History & Reports];
            BuyerDashboard --> BD13[Manage Profile & Department];
            BuyerDashboard --> BD14[Help & Support];
        end
    end'''
