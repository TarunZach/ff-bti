# ff-bti

Formulas



1.	Validation: 

For atstrik: In Required- If(IsBlank(DataCardValue15.Text),true,false)

For border colour: In BorderColour- If(IsMatch(DataCardValue18.Text,Match.Email), Color.Black, Color.Red)

Submit: In OnSelect- SubmitForm(Form6); Navigate(Success)



2.	Login Check

For Password: Mode: TextMode.Password

For Submit: OnSelect- If(!IsBlank(LookUp(LoginCheckPass,Username=TextInput1.Text And Password=TextInput1_1.Text)),Navigate(Success),UpdateContext({ShowForgetMessage:true}))

For extra label: Overflow- Hidden

Visible- ShowForgetMessage

 

3.	Cascading

For Degree: in Items- Distinct (DegreeCourse, Degree)

For course: In items- Filter(DegreeCourse, Degree = Dropdown2.Selected.Value)

Value- depends on dropdown2



4.	Autofill

For email: Dropdown- In Items- Distinct((AutoFill,Email)

In OnChange- Set(Values,LookUp(AutoFill,Email = Dropdown3.Selected.Value))

For Name: In default- Values.Name/ Values.Lastname



5.	Autosuggest

VerticalGallery: In items- Search(AutoFill, TextInput5.Text, "Name","LastName")



6.	Crud

VerticalGallery Form: OnSelect- ViewForm(Form1)

Form: Item- Gallery1.Selected

Default Mode- FormMode.New

Add: OnSelect- NewForm(Form1)

Edit: OnSelect- EditForm(Form1)

Submit: OnSelect- SubmitForm(Form1

Delete: OnSelect- Remove(AutoFill,ThisItem);Notify("Record Deleted",NotificationType.Information)



7.	Local Variable

InputBox: Display Mode → Edit

Button: Onselect- UpdateContext({FName:TextInput7.Text})

Extralabel: Text: FName



8.	Global Variable

Set(globall, TextInput2.Text);

Navigate(Success)



9.	Collection Variable

Collect(myCollection, {Product:TextInput4.Text, Price:TextInput3.Text})



10.	Patch - for updating a data

Patch(
    Appointments,
    LookUp(Appointments, Title = DataCardValue15.Text && Location = DataCardValue19.Text),
    {
        Status: DataCardValue4.Selected
    }
);

Navigate('Admin Dashboard', ScreenTransition.CoverRight);


11. Patch - for adding new data

Patch(
    Appointments,
    Defaults(Appointments),
    {
        Title: DataCardValue8.Text,
        'Start Time': DataCardValue9.SelectedDate,
        'End Time': DataCardValue10.SelectedDate,
        Status: DataCardValue11.Selected,
        Location: DataCardValue12.Text,
        Description: DataCardValue13.Text
    }
);
ResetForm(Form2);
Navigate('Admin Dashboard', ScreenTransition.CoverRight);










PHOTOS



INVENTORY MANAGEMENT PAD





BASIC RECORDER



LeaveReq-Cloud

