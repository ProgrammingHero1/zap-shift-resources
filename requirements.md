# <u>ZAPSHIFT - Dashboard Requirements </u>

---

## <u>Overview</u>

1. **ZAPSHIFT** is a home/office pickup parcel delivery system that streamlines booking, tracking, and delivery processes.
2. It offers tracking, delivery, and digital proof of delivery, enhancing efficiency and customer satisfaction.
3. Designed for businesses, it simplifies logistics while ensuring fast, reliable, and transparent delivery operations.

---

## <u>User Roles</u>

1. The **ZAPSHIFT** system is designed around three core user roles — **User**, **Admin**, and **Rider** — each responsible for distinct stages in the parcel delivery process.
2. Their coordinated efforts ensure a seamless end-to-end logistics experience across Bangladesh.

---

### 🧑‍💼 <u>1. User</u>

1. **Users** are registered users who initiate parcel deliveries through the platform. Their responsibilities include:

   1. Creating and submitting parcel booking requests with accurate type, weight, destination, and contact details.
   2. Making payment based on dynamic pricing calculated by the system.
   3. Receiving a unique tracking ID for each parcel.
   4. Monitoring parcel status in real-time.
   5. Reviewing the service after successful delivery to provide feedback and improve system quality.

---

### 🛠️ <u>2. Admin</u>

1. **Admins** are system operators responsible for managing parcel logistics and overseeing operational efficiency. Their key functions include:

   1. Assigning pickup riders and setting estimated delivery dates.
   2. Managing inter-district parcel routing and coordinating service center operations.
   3. Assigning delivery riders for last-mile delivery at the destination.
   4. Monitoring parcel movement, rider performance, and overall system operations.

---

### 🚚 <u>3. Rider</u>

1. **Riders** are responsible for the physical handling and movement of parcels.

   1. **Within City**

      1. Collect parcels directly from users.
      2. Update the system to reflect transit and delivery readiness.
      3. Deliver parcels to customers.
   2. **Outside City**

      1. Collect parcels directly from users.
      2. Submit collected parcels to the origin district service center.
      3. Deliver parcels to customers.

---

## <u>Dashboard Requirements</u>

### <u>Layouts</u>

1. The System will have a simple **Responsive Dashboard**.

   1. **A Sidebar at the Left**

      1. Contain logo, User Info such as Name, Image, Email, Role
      2. Some Dynamic Navigation Links based on user Role
      3. Navigation for Public Interfaces (Home, Coverage, etc)
      4. **LogOut Button**, on Clicking It user will be logged out
   2. **Pages at the Right**

      1. Pages will be show dynamically based on Routes

---

### <u>User Home (User)</u>

1. **States**: Show Some States about user all parcels

   1. unpaid
   2. paid
   3. ready-to-pickup
   4. in-transit
   5. reached-service-center
   6. shipped
   7. ready-to-delivery
   8. delivered

2. **Rechart & User Info**:

   1. Show User info such as name, email, photo URL and an edit button with Card Format at the left
   2. Show a Pie Chart with states value at the right

---

### <u>Tracking</u>

1. All the documents from the tracking collection where the sender is the user.
2. Show data in a 1 column notification format with a view details button.

---

### <u>Add Parcel (User)</u>

1. As the system is based on Door to Door delivery, Parcel needs both pickup and delivery location.

2. Will have a Heading & a subtitle

3. A Form with Multiple input field divided into 3 sub section

   1. **Parcel Info (3)**:

      1. type (document, non-document), title, weight (if type non-document)
   2. **Sender info (6)**:

      1. Name (prefilled), contact
      2. Select Region, Select Service Center
      3. Address, Pick up Instruction
   3. **Receiver info (6)**:

      1. Name, contact
      2. Select Region, Select Service Center
      3. Address, Delivery Instruction

4. Each of the fields are required except parcel weight

5. The cost will be calculated based on type, service center & weight.

6. On Clicking Submit Show user a Toast with Delivery Cost and a confirmation button. By clicking confirm, save the parcel info into the database with a creation\_date

---

### <u>Parcel To Pay (User)</u>

1. Show Total Parcel Found
2. Show a Search bar with a button to find parcels based on phone number.
3. Show all the parcels in a table format of user where sender is user & status is unpaid
4. Show important data such as, parcel Name, receiver info, cost, receiver address, etc.
5. Show some Actionable button

   1. **Pay** → Take user to ("/pay/parcelID") payment page
   2. **Delete** → (will delete after confirmation)
   3. **View** → ("/pay/parcelID") Take user to parcel details

---

### <u>Parcel Details Page (User, Admin, Rider)</u>

1. Show users all the details of the parcel.
2. if no parcel found show user that parcel not Found

---

### <u>Payment Page (User)</u>

1. **Total Charge to Pay**
2. Integrate a Card Based Payment System
3. On Successful payment

   1. Save Payment Info
   2. Add a 6 digit unique tracking\_no to the parcel
   3. Insert a tracking\_doc to the tracking\_collection
   4. Show a Success Alert with Tracking\_No & Transaction

---

### <u>Manage Parcel (User)</u>

1. A search feature based on receiver mobile number
2. Show all the parcel in a table format
3. Each row will have some required information with 2 button

   1. **Track**: will open a modal with tracking information / Take user to the tracking page
   2. **View**: will navigate users to parcel details information

---

### <u>Payment History (User)</u>

1. Show all payments made by the user in a table format.
2. The table will have payment info with Date Distance (ex. 13 days ago)

---

### <u>Discussion (User)</u>

1. Show an Add Review Button with an input field and a rating
2. Disable Add review Button if user have zero paid parcel
3. show all the reviews on the system
4. If the reviewer is a current user, show a 3 dot icon with a drop down, update, delete. Button. Implement, update and delete features.

---

### <u>User Settings (User, Rider, Admin)</u>

1. A Page from where a user can change his info such as update his image, name, password.
2. If Role Rider Show All the Data of Rider & Add update feature

---

## <u>Admin Dashboard</u>

---

### <u>Admin Home (Admin)</u>

1. **States**: Customer, Riders, Parcel Delivered, Service Centers, Earning
2. **Recharts**: Show a Rechart of service centers with a graph of the payments / Parcel Count
3. **Payment History**: Show all the payments in a notification format.

---

### <u>Manage Users (Admin)</u>

1. Search feature based on user email address
2. Filter feature based on role
3. List of all users with role, user & admin on the database in a table format with conditional button Make Admin if User, Make User if Admin
4. On clicking Admin user role will be an admin with confirmation alert.

---

### <u>Manage Rider (Admin)</u>

1. Show All riders in the system in a table

2. Add some conditional button based on status

   1. **Approve** (if pending / reject)
   2. **Reject** (If approved)

3. By clicking approve the Rider status will be approved & user role will be rider

4. By clicking Reject the Rider status will be reject & user role will be user

---

### <u>Delivery Management (Admin)</u>

1. Show States based on Parcel Status

2. Show all the Parcel Counts

3. A search System based on tracking\_no

4. Show Parcel Info such as Origin, destination, Tracking\_no, status, date, Actionable buttons (view, Manage)

   1. **View** will take user to parcel Details
   2. **Manage** will take user to manage Parcel Delivery Route
   3. Disable Manage Button (if status is unpaid)

5. **Parcel Statuses:**

   1. unpaid
   2. paid
   3. ready-to-pickup
   4. in-transit
   5. reached-service-center
   6. shipped
   7. ready-for-delivery
   8. delivered

---

### <u>Manage Parcel Delivery (Admin)</u>

1. Show Parcel Title as Title and a subtitle

2. Show Origin and Destination service center

3. Show parcel Details, Delivery Timeline (tracking Data)

4. Show Buttons & Cards based on status with a Ordered-List

   1. **Assign Parcel for PickUp** (enable it when status == paid)
   2. **Parcel Recived by Rider Card** (Show it when status == ready-to-pickup)
   3. **Confirm Parcel Recieved** (show it if service centers are different & enable it when status == in-transit)
   4. **Ship Parcel** (show it if service centers are different & enable it when status == reached-service-center)
   5. **Assign Parcel for Delivery** (show it if service centers are different & enable it when status == shipped)
   6. **Parcel Delivery by Rider Card** (Show it when status == ready-for-delivery)
   7. **Parcel Delivery Successfull Card** (Show it when status == delivered)

5. **Button Functionalities**

   1. **Assign Parcel for PickUp**:

      1. Shoow a Modal with pickup service center Info, Rider who works in the service center
      2. On Select a Rider Card Show Assign Button
      3. On Clicking Assign Rider email will be add on pickupRider, status will be ready-to-pickup, and a Tracking Doc will be created with relevant status message & date

   2. **Confirm Parcel Recieved**

      1. On Clicking it status will be changed to "reached-service-center"
      2. and a Tracking Doc will be created with relevant status message & date

   3. **Ship Parcel**

      1. On Clicking it status will be changed to "shipped"
      2. and a Tracking Doc will be created with relevant status message & date

   4. **Assign Parcel for Delivery**

      1. Shoow a Modal with delivery service center Info, Rider who works in the service center
      2. On Select a Rider Card Show Assign Button
      3. On Clicking Assign Rider email will be add on deliveryRider, status will be ready-for-delivery, a Tracking Doc will be created with relevant status message & date

---

## <u>Rider Dashboard</u>

---

### <u>Rider Home (Rider)</u>

1. **States**: Earning, Parcel to Deliver, Parcel to PickUp

2. **Rechart & User Info**:

   1. Show Rider info with name, email, photo URL, and an edit button with Card Format at the left. on Clicking it take user to the user settings route.
   2. Show a Pie Chart with states value at the right

3. **Current Task's**: Show all the tracking docs where status is "ready-to-pickup" or "ready-for delivery" & deliveryRider / pickUp rider is user with date.

---

### <u>Parcel-to-PickUp (Rider)</u>

1. Show Parcels where pickUp rider is user and status "ready-to-pickup" in a table format with address, sender contact and info and date
2. Add a button **Confirm PickUp**. On Clicking It, show Modal with Confirm Tracking\_no Input and Confirm button. On writing correct tracking\_no do some action
3. Parcel status will be changed to "in-transit" ( if the origin & destination service center different ) / "ready-for-delivery" ( if the origin & destination service center same )
4. a new tracking doc will be stored in tracking with a status message
5. Rider Earning will be increased by 20.

---

### <u>Parcel-to-Delivery (Rider)</u>

1. Show Parcels where delivery rider is user and status "ready-for-delivery" in a table format with address, receiver contact and info, and date
2. Add a button **Confirm Delivery**. On Clicking It, show Modal with Confirm Tracking\_no Input and Confirm button. On writing correct tracking\_no do some action
3. Parcel status will be changed to "delivered". A new tracking doc will be stored in tracking with a status message
4. Rider Earning will be increased by 20.

---

