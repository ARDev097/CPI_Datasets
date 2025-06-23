## **File Descriptions and Their Purpose**

### **1\. Data Folder**

#### **a) Councils\_and\_Committees\_Data**

Contains membership data for different councils and committees. Each file follows this structure:

* **member**: Name of the member.  
* **address**: Identifier address.  
* **start\_date**: Date when the season started.  
* **end\_date**: Date when the season ended.  
* **season**: The governance season during which the member was active.

#### **b) RPGF\_Rounds\_Data**

Contains data on retroactive public goods funding (RPGF) rounds. Each file includes:

* **address**: Wallet address of the badgeholder / citizen.  
* **start\_date**: Date when the round started.  
* **end\_date**: Date when the round ended.

#### **c) Data\_Sheets**

Contains daily data sheets where delegates’ voting power and their memberships in various councils and committees are recorded based on active seasons and RPGF rounds.

Data sheet structure

* **delegate**: Represents the name or identifier of the delegate in the governance system.  
* **voting\_power**: The voting power of the delegate in the general governance system.  
* **th\_vp**: The voting power of the delegate in the Token House (th\_vp stands for token house voting power).  
* **ch\_member\_r2**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Citizen House Round 2\. If the delegate is a member, the value is 1; otherwise, it is 0\.  
* **ch\_vp\_r2**: The voting power of the delegate in Citizen House Round 2 (ch stands for Citizen House). This value represents how much voting power the delegate has within this specific round.  
* **ch\_member\_r3**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Citizen House Round 3\. If yes, it is 1; otherwise, 0\.  
* **ch\_vp\_r3**: The voting power of the delegate in Citizen House Round 3\.  
* **ch\_member\_r4**: A binary indicator (1 or 0\) showing whether the delegate is a member of Citizen House Round 4\.  
* **ch\_vp\_r4**: The voting power of the delegate in Citizen House Round 4\.  
* **ch\_member\_r5**: A binary indicator (1 or 0\) showing whether the delegate is a member of Citizen House Round 5\.  
* **ch\_vp\_r5**: The voting power of the delegate in Citizen House Round 5\.  
* **ch\_member\_r6**: A binary indicator (1 or 0\) showing whether the delegate is a member of Citizen House Round 6\.  
* **ch\_vp\_r6**: The voting power of the delegate in Citizen House Round 6\.  
* **ch\_member\_r7**: A binary indicator (1 or 0\) showing whether the delegate is a member of Citizen House Round 7\.  
* **ch\_vp\_r7**: The voting power of the delegate in Citizen House Round 7\.  
* **gc\_member\_s3**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Grants Council Season 3 (gc stands for 
Grants Council).  
* **gc\_vp\_s3**: The voting power of the delegate in Grants Council Season 3\.  
* **gc\_member\_s4**: A binary indicator (1 or 0\) showing whether the delegate is a member of Grants Council Season 4\.  
* **gc\_vp\_s4**: The voting power of the delegate in Grants Council Season 4\.  
* **gc\_member\_s5**: A binary indicator (1 or 0\) showing whether the delegate is a member of Grants Council Season 5\.  
* **gc\_vp\_s5**: The voting power of the delegate in Grants Council Season 5\.  
* **gc\_member\_mm\_s5**: A binary indicator (1 or 0\) showing whether the delegate is a member of Grants Council Milestone & Metrics Subcommittee Season 5\.  
* **gc\_vp\_mm\_s5**: The voting power of the delegate in Grants Council Milestone & Metrics Subcommittee Season 5\.  
* **sc\_member\_s5**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Security Council Season 5 (sc stands for Security Council).  
* **sc\_vp\_s5**: The voting power of the delegate in the Security Council Season 5\.  
* **coc\_member\_s5**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Code of Conduct Council Season 5 (coc stands for Code of Conduct Council).  
* **coc\_vp\_s5**: The voting power of the delegate in the Code of Conduct Council Season 5\.  
* **dab\_member\_s5**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Developer Advisory Board Season 5 (dab stands for Developer Advisory Board).  
* **dab\_vp\_s5**: The voting power of the delegate in the Developer Advisory Board Season 5\.  
* **gc\_member\_s6**: A binary indicator (1 or 0\) showing whether the delegate is a member of Grants Council Season 6\.  
* **gc\_vp\_s6**: The voting power of the delegate in Grants Council Season 6\.  
* **gc\_member\_mm\_s6**: A binary indicator (1 or 0\) showing whether the delegate is a member of Grants Council Milestone & Metrics Subcommittee Season 6\.  
* **gc\_vp\_mm\_s6**: The voting power of the delegate in Grants Council Milestone & Metrics Subcommittee Season 6\.  
* **sc\_member\_s6**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Security Council Season 6\.  
* **sc\_vp\_s6**: The voting power of the delegate in the Security Council Season 6\.  
* **coc\_member\_s6**: A binary indicator (1 or 0\) showing whether the delegate is a member of the Code of Conduct Council Season 6\.

#### **d) Delegates\_Data**

Daily CSV files containing:

* **delegate**: Wallet address.  
* **voting\_power**: The delegate’s voting power on that specific day.

#### **e) Delegates\_Data\_with\_ACC\_Members**

Daily CSV files where Anticapture Commission (ACC) members are added, and ACC is removed as a separate delegate. Voting power is equally distributed among all members.

* **delegate**: Wallet address.  
* **voting\_power**: The delegate’s voting power on that specific day.

## **2\. Python Files and Their Functions**

### **a) add\_acc\_members.ipynb**

**Purpose**: Modifies delegate data by incorporating Anticapture Commission members.

* Reads the daily **Delegates\_Data**.  
* Adds members from **Anticapture\_Commission.csv**.  
* Removes ACC as a separate delegate and distributes its power among its members.  
* Saves the modified data into **Delegates\_Data\_with\_ACC\_Members**.

### **b) create\_data\_sheets.ipynb**

**Purpose**: Generates daily data sheets with voting power and membership details.

* Reads delegate data from **Delegates\_Data\_with\_ACC\_Members**.  
* Assigns council/committee memberships based on active seasons and RPGF rounds.  
* Creates a new dataset combining voting power and membership information.  
* Saves the output to **Data\_Sheets**.

### **c) calculate\_HHI\_and\_CPI.ipynb**

**Purpose**: Computes HHI (Herfindahl-Hirschman Index) and CPI (Concentration of Power Index).

* Reads daily data sheets from **Data\_Sheets**.  
* Calculates **HHI** by summing the squares of delegate voting power in Token House.  
* Computes **CPI** based on adjusted voting power metrics.  
* Saves the output into a CSV file containing daily CPI and HHI values.

## **How to Modify or Update Data**

### **Step 1: Updating Membership Data**

* If new members join a council or committee, update the corresponding CSV file in **Councils\_and\_Committees\_Data**.  
* Ensure that the **start\_date** and **end\_date** fields are correctly assigned.

### **Step 2: Adding New RPGF Rounds**

* Create a new CSV file under **RPGF\_Rounds\_Data** for the new round.  
* Use the same column structure (**address, start\_date, end\_date**).

### **Step 3: Modifying Delegate Voting Power**

* Update the daily CSV files in **Delegates\_Data** if a delegate’s voting power changes.

### **Step 4: Running Python Scripts After Changes**

After making changes to any data files, execute the following scripts in order:

1. **add\_acc\_members.ipynb** – Updates delegate data by incorporating ACC members.  
   * Reads the daily **Delegates\_Data**.  
   * Adds members from **Anticapture\_Commission.csv**.  
   * Removes ACC as a separate delegate and distributes its power among its members.  
   * Stores the modified data in the folder named **Delegates\_Data\_with\_ACC\_Members**.  
       
2. **create\_data\_sheets.ipynb** – Generates the daily data sheets with voting power and membership.  
   * Reads delegate data from **Delegates\_Data\_with\_ACC\_Members**.  
   * Assigns council/committee memberships based on active seasons and RPGF rounds.  
   * Creates a new dataset combining voting power and membership information.  
   * Stores the data sheets in the folder named **Data\_Sheets**.  
       
3. **calculate\_HHI\_and\_CPI.ipynb** – Computes the daily HHI (Herfindahl-Hirschman Index)  and CPI (Concentration of Power Index).  
   * Reads daily data sheets from **Data\_Sheets**.  
   * Computes the influence of each delegate and based on that calculates the HHI and CPI for each day.  
   * Stores the results in a CSV file named **daily\_hhi\_and\_cpi.csv**.  
   * This file uses the influence of each **House, Council, or Committee (HCC)** in CPI calculation, which are mentioned inside the influence periods list in the **calculate\_HHI\_and\_CPI.ipynb** file. These values can be changed inside that list if necessary.

   

