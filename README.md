 1. Plasma BOOKING SYSTEM
A. Create these controls
TextBoxes
txtGuestName
txtGuestAge
txtNights
txtGuests
ComboBox
cmbRoomType — Standard, Normal, Hight
CheckBox
chkBreakfast
Buttons
btnCalculate
btnClear
btnExit
Label
lblResult
B. Complete C# code
using System;
using System.Windows.Forms;

namespace HotelBookingSystem
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();

            cmbRoomType.Items.Add("Standard");
            cmbRoomType.Items.Add("Normal");
            cmbRoomType.Items.Add("Hight");
        }

        private void btnCalculate_Click(object sender, EventArgs e)
        {
            string guestName = txtGuestName.Text.Trim();

            if (guestName == "")
            {
     …
 2. HOTELL . Star BOOKING SYSTEM
A. Create these controls
TextBoxes
txtPassengerAge
txtTickets
txtBaggageWeight
txtTicketPrice
ComboBox
cmbTravelClass — Economy, Business, First Class
CheckBox
chkInsurance
Buttons
btnCalculate
btnClear
btnExit
Label
lblResult
B. Complete C# code
using System;
using System.Windows.Forms;

namespace TicketBookingSystem
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();

            cmbTravelClass.Items.Add("Economy");
            cmbTravelClass.Items.Add("Business");
            cmbTravelClass.Items.Add("First Class");
        }

        private void btnCalculate_Click(object sender, EventArgs e)
        {
            if (!int.TryParse(txtPassengerAge.Text, out int ag…

            3. RENTAL MOTORS MANAGEMENT SYSTEM
This assignment requires you to check whether a customer is eligible to rent a vehicle and calculate the rental cost.
A. Create these controls
TextBoxes
txtCustomerName
txtCustomerAge
txtRentalDays
txtDrivingExperience
ComboBox
cmbVehicleType — Economy, SUV, Luxury
CheckBox
chkInsurance
Buttons
btnCalculate
btnClear
btnExit
Label
lblResult
B. Complete C# code
using System;
using System.Windows.Forms;

namespace VehicleRentalSystem
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();

            cmbVehicleType.Items.Add("Economy");
            cmbVehicleType.Items.Add("SUV");
            cmbVehicleType.Items.Add("Luxury");
        }

        private void btnCalculate_Click(object sender, EventArgs e)
        {
            string customerName = txtCustomerName.Text.Trim();

            if (customerName == "")
            {
                MessageBox.Show("Enter customer name.");
                return;
            }

            if (!int.TryParse(txtCustomerAge.Text, out int age) ||
                !int.TryParse(txtRentalDays.Text, out int days) ||
                !int.TryParse(txtDrivingExperience.Text, out int experience))
            {
                MessageBox.Show("Enter valid numeric values.");
                return;
            }

            if (age < 18 || age > 80)
            {
                MessageBox.Show("Age must be between 18 and 80.");
                return;
            }

            if (days < 1 || days > 30)
            {
                MessageBox.Show("Rental days must be between 1 and 30.");
                return;
            }

            if (experience < 0)
            {
                MessageBox.Show("Driving experience cannot be negative.");
                return;
            }

            if (age < 21)
            {
                MessageBox.Show("Customers below 21 cannot rent vehicles.");
                return;
            }

            if (experience < 1)
            {
                MessageBox.Show("At least 1 year of driving experience is required.");
                return;
            }

            if (cmbVehicleType.SelectedIndex == -1)
            {
                MessageBox.Show("Select a vehicle type.");
                return;
            }

            if (cmbVehicleType.Text == "Luxury" &&
                (age < 25 || experience < 3))
            {
                MessageBox.Show(
                    "Luxury vehicles require age 25 or above " +
                    "and at least 3 years of driving experience.");

                return;
            }

            double dailyRate = 0;

            switch (cmbVehicleType.Text)
            {
                case "Economy":
                    dailyRate = 35;
                    break;

                case "SUV":
                    dailyRate = 60;
                    break;

                case "Luxury":
                    dailyRate = 100;
                    break;
            }

            double basicCost = dailyRate * days;

            double discount = 0;

            if (days >= 14)
                discount = basicCost * 0.10;
            else if (days >= 7)
                discount = basicCost * 0.05;

            double insuranceCost = 0;

            if (chkInsurance.Checked)
                insuranceCost = 15 * days;

            double youngDriverSurcharge = 0;

            if (age >= 21 && age <= 24)
                youngDriverSurcharge = basicCost * 0.10;

            double total = basicCost - discount
                         + insuranceCost + youngDriverSurcharge;

            lblResult.Text =
                "Customer Name: " + customerName +
                "\nVehicle Type: " + cmbVehicleType.Text +
                "\nRental Days: " + days +
                "\nBasic Rental Cost: " + basicCost.ToString("C2") +
                "\nDiscount: " + discount.ToString("C2") +
                "\nInsurance: " + insuranceCost.ToString("C2") +
                "\nYoung Driver Surcharge: " +
                youngDriverSurcharge.ToString("C2") +
                "\nFinal Rental Cost: " + total.ToString("C2");
        }

        private void btnClear_Click(object sender, EventArgs e)
        {
            txtCustomerName.Clear();
            txtCustomerAge.Clear();
            txtRentalDays.Clear();
            txtDrivingExperience.Clear();

            cmbVehicleType.SelectedIndex = -1;
            chkInsurance.Checked = false;

            lblResult.Text = "";
        }

        private void btnExit_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }
    }
}
 4. THE COURSE REGISTRATION FEE SYSTEM
This project calculates a student's registration fee according to their study year, number of courses, accommodation, and transport.
A. Create these controls
TextBoxes
txtStudentName
txtStudentID
txtCourses
ComboBox
cmbStudyLevel — Year 1, Year 2, Year 3, Year 4
CheckBoxes
chkAccommodation
chkTransport
Buttons
btnCalculate
btnClear
btnExit
Label
lblResult
B. Complete C# code
using System;
using System.Windows.Forms;

namespace CourseRegistrationSystem
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();

            cmbStudyLevel.Items.Add("Year 1");
            cmbStudyLevel.Items.Add("Year 2");
            cmbStudyLevel.Items.Add("Year 3");
            cmbStudyLevel.Items.Add("Year 4");
        }

        private void btnCalculate_Click(object sender, EventArgs e)
        {
            string studentName = txtStudentName.Text.Trim();
            string studentID = txtStudentID.Text.Trim();

            if (studentName == "" || studentID == "")
            {
                MessageBox.Show("Enter student name and ID.");
                return;
            }

            if (!int.TryParse(txtCourses.Text, out int courses))
            {
                MessageBox.Show("Enter a valid number of courses.");
                return;
            }

            if (courses < 1 || courses > 8)
            {
                MessageBox.Show("Courses must be between 1 and 8.");
                return;
            }

            double feePerCourse = 0;

            switch (cmbStudyLevel.Text)
            {
                case "Year 1":
                    feePerCourse = 40;
                    break;

                case "Year 2":
                    feePerCourse = 45;
                    break;

                case "Year 3":
                    feePerCourse = 50;
                    break;

                case "Year 4":
                    feePerCourse = 55;
                    break;

                default:
                    MessageBox.Show("Select a study level.");
                    return;
            }

            double tuitionFee = feePerCourse * courses;

            double accommodationFee = 0;

            if (chkAccommodation.Checked)
                accommodationFee = 120;

            double transportFee = 0;

            if (chkTransport.Checked)
                transportFee = 50;

            double subtotal = tuitionFee
                            + accommodationFee
                            + transportFee;

            double courseDiscount = 0;

            if (courses >= 6)
                courseDiscount = tuitionFee * 0.10;

            double serviceDiscount = 0;

            if (chkAccommodation.Checked &&
                chkTransport.Checked &&
                courses >= 5)
            {
                serviceDiscount = tuitionFee * 0.05;
            }

            double totalDiscount = courseDiscount + serviceDiscount;

            double finalFee = subtotal - totalDiscount;

            lblResult.Text =
                "Student Name: " + studentName +
                "\nStudent ID: " + studentID +
                "\nStudy Level: " + cmbStudyLevel.Text +
                "\nNumber of Courses: " + courses +
                "\nTuition Fee: " + tuitionFee.ToString("C2") +
                "\nAccommodation Fee: " +
                accommodationFee.ToString("C2") +
                "\nTransport Fee: " + transportFee.ToString("C2") +
                "\nCourse Discount: " + courseDiscount.ToString("C2") +
                "\nService Discount: " + serviceDiscount.ToString("C2") +
                "\nTotal Discount: " + totalDiscount.ToString("C2") +
                "\nFinal Registration Fee: " + finalFee.ToString("C2");
        }

        private void btnClear_Click(object sender, EventArgs e)
        {
            txtStudentName.Clear();
            txtStudentID.Clear();
            txtCourses.Clear();

            cmbStudyLevel.SelectedIndex = -1;

            chkAccommodation.Checked = false;
            chkTransport.Checked = false;

            lblResult.Text = "";
        }

        private void btnExit_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }
    }
}
