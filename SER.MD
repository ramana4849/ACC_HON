
1. OBY6 - to check all company codes
#### Creation of company code 

- SPRO -> SAP Image REF 

- Enterprise Structure -> Definition -> Financial Accounting -> Edit,copy,delete and check company code 

```
example:

from company code: 4001 0R 1404
to company code: THSC 

```
- click create request and edit description 
- CHANGE COMPANY NAME
- check company code with OBY6.


#### Creation of cost and profit center 
- creation of profit center(ke51)
   ```
   example:
   PC: THSPRO
   CO Area:6000

   copy from
   PC:11100101
   CO Area:600
   ```
   Assign company code and click save
   - creation of cost center(ks01)
   ```
   example:

   CO Area:6000
   CC: THSCOS
   Valid from: 01.01.2019 to 31.12.9999

   reference

   CC: 40012001
   CO: 6000

   ```
   Accounting -> joint venture accounting
- change company code and profit center and click save option

#### MM 
  - Define the Plant code and change name of plant code 
   ```
   Enterprise Structure -> Definition -> Logistics General -> copy,delete and check plant 

   example:

   copy plant: 4111
   to plant : THSC 

    Change name of Plant
   ```

  - Define Storage location
  ```
   Enterprise Structure → Definition → Materials Management → Maintain Storage Location
  ```
  - Define Purchasing Organisation
    ```
     Enterprise Structure → Definition → Materials Management → Maintain Purchasing Organization
    ```
  - Assign the Plant to the Company Code 
   ```
    Enterprise Structure → Assignment → Logistics - General → Assign plant to company code
   ```
  - Assign the Purchase Organization to the Plant
    ```
    Enterprise Structure → Assignment → Materials Management → Assign purchasing
    organization to plant
    ```
  
#### SD 
  - Define the Sales Organization(Ref-4100)
  ```
    Enterprise Structure → Definition → Sales and Distribution → Define, copy, delete , check sales organization

   - Change name of sales orginsation
  ```

- Define the Distribution Channel
- Define the Division
- Define the Shipping Point (Required for SAP TM Integration)
- Assign Sales Organization to Company Code

  ```
  Enterprise Structure → Assignment → Sales and Distribution → Assign sales organization
  to company code

  ```

- Assign Distribution Channel to Sales Organization
- Assign Division to Sales Organization
- Set Up the Sales Area
- Cross-Module Integration: Assign Sales Organization / Distribution Channel to Plant
   

1. creation of purchase group 
   ```
   SPRO -> SAP reference img -> Materials Mangement -> Purchasing -> Create purchasing group

   click new enteries and save 
  
   (KNR || ASRC BUYER GROUP)
   

   ```

2. creation of orginazational model
   to open organisational model "PPOME"

   ```
   SPRO -> SAP reference img -> Transportation Mangement -> master data -> Organisational management -> organisational Model 

   ``` 


3.  Activation of ledger plant(omx3,omx2,omx1,CKMSTART)
    - SE38 or SE32-TO decativate plant (SAPRCKMJX)
4.  creation of material master(mm01)
5.  Creation of BP (customer and carrier)8999999492
   - Customer - 0300004187
   - BP (00000)-> Customer(FLCU00) ->customer (FLCU01) 
   - carrier - 0300004189
   - BP(00000) -> Supplier(FLVN00) -> Supplier(FVLVN01) -> Carrier(CRM010)
6. Define LIP
    - Control keys (SPRO -> SAP ref IMG -> TM -> INTEGRATION ->LOGISTICS INTEGRATION -> INTERNAL TM)
    - Define LIP(under we have FUBR blank )
    - Define Transportation relevance of sales Document (edit seen enteries)

7.  creation of frieght Unit type
    - SPRO -> SAP img REF -> Transportation Mangement -> Planning -> Frieght unit -> define frieght unit types
    - after creation with ref-0001 and go to firori screen and open edit fubr.
    - enter "AVRC" in document type and save
    - create another sales area(VA01)
  


9.  Define Means of transport 
    - (TM-> master data -> resouces -> Means of transport and compartment -> Define means of tarnsport)
  
     ```
     example : TRUCK_YOURCC

     ```

    - create resources (till Transportation cockpit its okay)
    - (SAP Menu -> Logistics -> TM -> Master Data -> Resource )
    
    ```
    BOX_TRUCK
    FLATBED_TRUCK
    TANK_TRUCK
    

    Enter location and means of transport contionous dim,factory calender,capacity,unit

    ```

        - define transportation lanes(/n/SCMTMS/TL5)(connecting means of transport to carrier)
        - define transportation zones(/n/SCMTMS/ZONE)(ZONE1,ZONE2)(defining souce and destination loactions as zones)
    - WE are extracting source location and destination loactioN by displaying frieght unit type

### (Transportation Cockpit)
   1.  Create selection profile 
    - selection profile 
    - time related selected attributs 
    - geographical selection attributes 
    - additional selection attributes 
   2. Planning Profile
      - Planning profile
 
   3. pagelayout for TC (used pre defined) 
   4. Profile and Layout settings (Profile and settings)  
   5. go to planning -> transportation cockpit 

### TCM(Transportation Charge Management)
- We are following Bottom -Up Approach
- Frieght Settlement Document(Calculation in Frieght order / Frieght booking )
- Goto Charge management
11. Create scale
    - _LOC(AVRC source location) as LOC 
    - _LOC(AVRC Destination location) as LOC
    - _GROSSWeight (AVRC Gross weight) as Weight 
12. create rate table Definition
    - Define rate table types
      SPRO -> sap img ref -> TM -> Master data -> Rate Tables -> Define Rate table type 
    
      
    - Define Charge Types 
       SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charge Types 
       A2CC_BASE_CHAR= BASEFRT (BASIC CHARGES)  
       YT_HA_FUEL = FUEL (FUEL CHARGES)
       YT_HA_STOP = BNR (BUNKER CHARGES)

    - create rate table definition(Friori screen) 55 mins 
       RT1 =BASIC CHARGES
       RT2 = FUEL CHARGES
       RT3 = BUNKER CHARGES 
       . General Data -> insert scales 
       . Update charge type for every rate table 

    

13. Charge calucation sheet - create calculation sheet 

  
14. Frieght agreement
     SPRO -> sap img ref -> TM -> master data -> Agreement and service product -> define frieght Agreement Types

    - Create Frieght Agreement (Contract manager) 
    


### Frieght settlement Document 
#### part-1 OKB9  OCT28 
1. Create Frieght settlement Document
   SPRO -> sap img ref -> TM -> settlement -> Frieght settlement -> Define Frieght settlement Document Type (ref: ZFUS)
    - Frieght settlement Document Type 
    - Update "FSD type"  in Frieght order type 
 
 
    - AC03 = Create Service master
      Activity Number

    SPRO -> Sap img ref -> TM -> Settlement -> Frieght settlement -> Integration for settlement posting -> Assign purchasing information for posting 
    - Assign purchasing information for posting (Assigning plant and purchase group here) 
    - Map transportation charge type to service master road (600,600000,AVRC_ROADFRT,3008143)


##### part-2 
SPRO -> sap img ref -> TM -> Settlement -> Define settlement profile (ref:ZSP_ROAD)
  - Define Frieght Settlement profile 

SPRO -> SAP img ref -> TM -> Basic functions -> Cost distribution -> Define cost distribution profile (ref: A2CC_C_DIS)
   - define cost Distribution profile
  
SPRO -> Sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define calculation profiles (ref:A2CCCALPRO)
   - Define calculation profiles 

SPRO -> sap img ref -> TM -> Basic functions -> Charge calculation -> basic settings -> Define charges profile
 - Define charges profile 
    - update the settlement profile 
    - update calculation profile 
    - update cost distribution profile 
  
- update in organisational model under purchase org AVRC 
- Go to BP under select carrier and go to general data and update CALCULATION PROFILE & Freight settlement Profile. 

####  Post frieght settlement document OCT29
 
 - goto frieght order type and click on create frieght settlement document 
 - Frieght settlement document




1. Accruals posted


GOTO SU3 Maintain user profile
- POK X 
- SCL G
- TM_INVOICE CLERK

SPRO -> SAP ref img -> Integration with other SAP components -> TM -> Invoice Integration -> Mapping for cost distribution -> Assing transportation charge types to condition types



MMPV - TCODE 
MIRO - to open invoice  screen 



 


### Assigning shipping point 

-  Enterprise Structure -> Definition -> Logistics Exceution -> Copy ,Delete and Check Shipping Plant 

```
example :
From shipping point:4111
to shipping point: THSC

```

-  Enterprise Structure → Definition → Logistics Execution → Define shipping point 
    (change name of shipping point) 

- Enterprise Structure -> Assignment -> Logistics Exceution -> Assign shipping point to plant 
   
   OR 

- SPRO -> SAP refernece img -> Logistics Execution → Shipping → Basic Shipping Functions →   Shipping Points and Goods Receiving Point Determination → Assign Shipping Point 
( Shipping Point Determination Backend Logic)











### synchronously process
1. Open transaction SE38.
2. Enter /SCMTMS/SFIR_TRANSFER_BATCH.
3. Click Execute (F8).
4. Enter the FSD number.
5. Enter the relevant FSD Type, Purchasing Organization and Purchasing Group.
6. Select the appropriate lifecycle status for eligible documents.
7. First run in Simulation Mode to check which documents are selected.
8. If the document is eligible, run the report without Simulation Mode.
9. Check the FSD Application Log and refresh its status.

 





  

