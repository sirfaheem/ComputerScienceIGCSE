Module Module1
    Sub Main()

    End Sub
    Sub TAsk1()

        Dim MaxStayHours(7) As Integer
        Dim ChargePerHour(7) As Decimal
        Dim DayNum As Integer
        Dim ValidDayNum As Boolean
        Dim ArrivalHour As Integer
        Dim ValidArrivalHour As Boolean
        Dim TimeNeeded As Integer
        Dim FrequentParkingNumber As String
        Dim TotalModulo11 As Integer
        Dim Num(5) As Integer
        Dim Discount As Boolean
        Dim ChargeToPark As Decimal
        Dim DiscountAmount As Decimal
        Dim Shift1 As Boolean


        MaxStayHours(1) = 8
        MaxStayHours(2) = 2
        MaxStayHours(3) = 2
        MaxStayHours(4) = 2
        MaxStayHours(5) = 2
        MaxStayHours(6) = 2
        MaxStayHours(7) = 4

        ChargePerHour(1) = 2.0
        ChargePerHour(2) = 10.0
        ChargePerHour(3) = 10.0
        ChargePerHour(4) = 10.0
        ChargePerHour(5) = 10.0
        ChargePerHour(6) = 10.0
        ChargePerHour(7) = 3.0

        Const MaxEveningStayHour = 7
        Const ChargePerHourEvening = 2.0
        ValidDayNum = False

        Do
            Console.WriteLine("1. Sunday")
            Console.WriteLine("2. Monday")
            Console.WriteLine("3. Tuesday")
            Console.WriteLine("4. Wednesday")
            Console.WriteLine("5. Thursday")
            Console.WriteLine("6. Friday")
            Console.WriteLine("7. Saturday")
            Console.Write("Enter day number [1-7]: ")
            DayNum = Console.ReadLine()

            ' Console.WriteLine("Enter valid Day Number")

        Loop Until DayNum < 7 And DayNum >= 1

        ValidArrivalHour = False



        Do
            Console.WriteLine("We Ae  Open from")
            Console.WriteLine("Enter the hour of your arrival ( Military Formate And Hour Only )")
            ArrivalHour = Console.ReadLine()
            
        Loop Until ArrivalHour >= 8 And ArrivalHour <= 23
        If ArrivalHour < 16 Then Shift1 = True
        Do
            If Shift1 = True Then
                Console.WriteLine("You can stay for " & Str(MaxStayHours(DayNum)) & " hours or less.")
            Else
                Console.WriteLine("You can stay for " & Str(MaxEveningStayHour) & " hours or less.")
            End If
            Console.Write("Enter hours to stay: ")
            TimeNeeded = Console.ReadLine

        Loop Until TimeNeeded <= MaxStayHours(DayNum) ''5434678798976543567890987654

        Discount = False
        Console.WriteLine("Enter your parking number ")
        FrequentParkingNumber = Console.ReadLine()
        ''çk
        For i = 5 To 1
            Num(i) = Val(Mid(FrequentParkingNumber, i, 1))
            TotalModulo11 = TotalModulo11 + (Num(i) * i)
        Next
        If TotalModulo11 Mod 11 = 0 Then Discount = True

        DiscountAmount = 0


        If Shift1 = True Then
            If Discount = True Then DiscountAmount = 0.1
            ChargeToPark = TimeNeeded * ChargePerHour(DayNum)
        Else
            If Discount = True Then DiscountAmount = 0.5
            ChargeToPark = TimeNeeded * ChargePerHourEvening
        End If


        ChargeToPark -= ChargeToPark * DiscountAmount
        Console.WriteLine("your ChargeToPark price is " & Str(ChargeToPark))


        Console.ReadKey()
    End Sub

    Sub Task2()

        Dim Days(7) As String
        Dim MaxStayHours(7) As Integer
        Dim ChargePerHour(7) As Decimal
        Dim DayNum As Integer
        Dim ValidDayNum As Boolean
        Dim ArrivalHour As Integer
        Dim ValidArrivalHour As Boolean
        Dim TimeNeeded As Integer
        Dim ValidTimeNeeded As Boolean
        Dim FrequentParkingNumber As String
        Dim TotalModulo11 As Integer
        Dim n(5) As Integer
        Dim Discount As Boolean
        Dim ChargeToPark As Decimal
        Dim DiscountAmount As Decimal
        Dim AmountReceived As Integer
        Dim ValidAmountReceived As Boolean
        Dim Dailytotal As Decimal
        Dim ShowDailyTotal As Char

        Days(1) = "Sunday"
        Days(2) = "Monday"
        Days(3) = "Tuesday"
        Days(4) = "Wednesday"
        Days(5) = "Thursday"
        Days(6) = "Friday"
        Days(7) = "Saturday"

        MaxStayHours(1) = 8
        MaxStayHours(2) = 2
        MaxStayHours(3) = 2
        MaxStayHours(4) = 2
        MaxStayHours(5) = 2
        MaxStayHours(6) = 2
        MaxStayHours(7) = 4

        ChargePerHour(1) = 2.0
        ChargePerHour(2) = 10.0
        ChargePerHour(3) = 10.0
        ChargePerHour(4) = 10.0
        ChargePerHour(5) = 10.0
        ChargePerHour(6) = 10.0
        ChargePerHour(7) = 3.0

        Const MaxEveningStayHour = 7
        Const ChargePerHourEvening = 2.0
        Dailytotal = 0
        Do
            ValidDayNum = False
            Do
                Console.WriteLine("1. Sunday")
                Console.WriteLine("2. Monday")
                Console.WriteLine("3. Tuesday")
                Console.WriteLine("4. Wednesday")
                Console.WriteLine("5. Thursday")
                Console.WriteLine("6. Friday")
                Console.WriteLine("7. Saturday")
                Console.Write("Enter day number: ")
                DayNum = Console.ReadLine()
                If DayNum > 7 Or DayNum < 1 Then
                    Console.WriteLine("Enter valid Day Number")
                Else
                    ValidDayNum = True
                End If
            Loop While ValidDayNum = False

            ValidArrivalHour = False
            Do
                Console.WriteLine("Enter the hour of your arrival ( Military Formate And Hour Only )")
                ArrivalHour = Console.ReadLine()
                If ArrivalHour < 8 Or ArrivalHour > 23 Then
                    Console.WriteLine("Sorry We Ae Not Open Now")
                    ValidArrivalHour = False
                Else
                    ValidArrivalHour = True
                End If
            Loop While ValidArrivalHour = False

            ValidTimeNeeded = False
            Console.WriteLine("your maximum hour stay can be " & Str(MaxStayHours(DayNum)))
            Do
                Console.WriteLine("Enter the Time Needed")
                TimeNeeded = Console.ReadLine()
                If ArrivalHour < 16 Then
                    If TimeNeeded > MaxStayHours(DayNum) Then
                        Console.WriteLine(" Sorry Too Long Stay Not Possible ")
                        ValidTimeNeeded = False
                    Else
                        ValidTimeNeeded = True
                    End If
                End If
                If ArrivalHour >= 16 Then
                    If TimeNeeded > MaxEveningStayHour Then
                        Console.WriteLine("Sorry Too LOng Stay ")
                        ValidTimeNeeded = False
                    Else
                        ValidTimeNeeded = True
                    End If
                End If
            Loop Until ValidTimeNeeded = True

            Console.WriteLine("Enter your parking number ")
            FrequentParkingNumber = Console.ReadLine()
            For i = 5 To 1
                n(1) = Val(Mid(i, 1))
                TotalModulo11 = TotalModulo11 + (n(i)) * i
            Next
            If TotalModulo11 Mod 11 = 0 Then
                Discount = False
            Else
                Discount = True
            End If
            DiscountAmount = 1
            If ArrivalHour < 16 Then
                ChargeToPark = TimeNeeded * ChargePerHour(DayNum)
            End If
            If ArrivalHour >= 16 Then
                ChargeToPark = TimeNeeded * ChargePerHourEvening
            End If
            If Discount = True And ArrivalHour >= 16 Then
                DiscountAmount = 0.5
            End If
            If Discount = True And ArrivalHour < 16 Then
                DiscountAmount = 0.1
            End If
            If Discount = False Then
                Console.WriteLine("Your Price to park is " & Str(ChargeToPark))
            End If
            If Discount = True Then
                ChargeToPark = ChargeToPark * DiscountAmount
                Console.WriteLine("your Discounted price is " & Str(ChargeToPark))
            End If

            ValidAmountReceived = False
            Do
                Console.WriteLine("Enter the amount paid by the customer ")
                AmountReceived = Console.ReadLine()
                If AmountReceived < ChargeToPark Then
                    Console.WriteLine("pay full amount ")
                    ValidAmountReceived = False
                Else
                    ValidAmountReceived = True
                End If
            Loop While ValidAmountReceived = False

            Dailytotal = Dailytotal + AmountReceived
            Console.WriteLine("Do you Want TO see The DAily Total")
            ShowDailyTotal = Console.ReadLine()
        Loop While ShowDailyTotal = UCase("N")
        Console.WriteLine("The Daily Total is " & Str(Dailytotal))

        Console.ReadKey()
    End Sub

    Sub Task3()
        Dim Days(7) As String
        Dim MaxStayHours(7) As Integer
        Dim ChargePerHour(7) As Decimal
        Dim DayNum As Integer
        Dim ValidDayNum As Boolean
        Dim ArrivalHour As Integer
        Dim ValidArrivalHour As Boolean
        Dim TimeNeeded As Integer
        Dim ValidTimeNeeded As Boolean
        Dim FrequentParkingNumber As String
        Dim TotalModulo11 As Integer
        Dim n(5) As Integer
        Dim Discount As Boolean
        Dim ChargeToPark As Decimal
        Dim DiscountAmount As Decimal
        Dim ExitHour As Decimal
        Dim EveningDisount As Decimal = 0.5
        Dim MorningDiscount As Decimal = 0.1

        Days(1) = "Sunday"
        Days(2) = "Monday"
        Days(3) = "Tuesday"
        Days(4) = "Wednesday"
        Days(5) = "Thursday"
        Days(6) = "Friday"
        Days(7) = "Saturday"

        MaxStayHours(1) = 8
        MaxStayHours(2) = 2
        MaxStayHours(3) = 2
        MaxStayHours(4) = 2
        MaxStayHours(5) = 2
        MaxStayHours(6) = 2
        MaxStayHours(7) = 4

        ChargePerHour(1) = 2.0
        ChargePerHour(2) = 10.0
        ChargePerHour(3) = 10.0
        ChargePerHour(4) = 10.0
        ChargePerHour(5) = 10.0
        ChargePerHour(6) = 10.0
        ChargePerHour(7) = 3.0

        Const MaxEveningStayHour = 7
        Const ChargePerHourEvening = 2.0
        ValidDayNum = False

        Do
            Console.WriteLine("1. Sunday")
            Console.WriteLine("2. Monday")
            Console.WriteLine("3. Tuesday")
            Console.WriteLine("4. Wednesday")
            Console.WriteLine("5. Thursday")
            Console.WriteLine("6. Friday")
            Console.WriteLine("7. Saturday")
            Console.Write("Enter day number: ")
            DayNum = Console.ReadLine()
            If DayNum > 7 Or DayNum < 1 Then
                Console.WriteLine("Enter valid Day Number")
            Else
                ValidDayNum = True
            End If
        Loop While ValidDayNum = False

        ValidArrivalHour = False
        Do
            Console.WriteLine("Enter the hour of your arrival ( Military Formate And Hour Only )")
            ArrivalHour = Console.ReadLine()
            If ArrivalHour < 8 Or ArrivalHour > 23 Then
                Console.WriteLine("Sorry We Ae Not Open Now")
                ValidArrivalHour = False
            Else
                ValidArrivalHour = True
            End If
        Loop While ValidArrivalHour = False

        ValidTimeNeeded = False
        Console.WriteLine("your maximum hour stay can be " & Str(MaxStayHours(DayNum)))
        Do
            Console.WriteLine("Enter the Time Needed")
            TimeNeeded = Console.ReadLine()
            If ArrivalHour < 16 Then
                If TimeNeeded > MaxStayHours(DayNum) Then
                    Console.WriteLine(" Sorry Too Long Stay Not Possible ")
                    ValidTimeNeeded = False
                Else
                    ValidTimeNeeded = True
                End If
            End If
            If ArrivalHour >= 16 Then
                If TimeNeeded > MaxEveningStayHour Then
                    Console.WriteLine("Sorry Too LOng Stay ")
                    ValidTimeNeeded = False
                Else
                    ValidTimeNeeded = True
                End If
            End If
        Loop Until ValidTimeNeeded = True

        Console.WriteLine("Enter your parking number ")
        FrequentParkingNumber = Console.ReadLine()
        For i = 5 To 1
            n(1) = Val(Mid(i, 1))
            TotalModulo11 = TotalModulo11 + (n(i)) * i
        Next
        If TotalModulo11 Mod 11 = 0 Then
            Discount = False
        Else
            Discount = True
        End If
        DiscountAmount = 1
        If ArrivalHour < 16 Then
            ChargeToPark = TimeNeeded * ChargePerHour(DayNum)
        End If
        If ArrivalHour >= 16 Then
            ChargeToPark = TimeNeeded * ChargePerHourEvening
        End If
        If Discount = True And ArrivalHour >= 16 Then
            DiscountAmount = 0.5
        End If
        If Discount = True And ArrivalHour < 16 Then
            DiscountAmount = 0.1
        End If
        If Discount = False Then
            Console.WriteLine("Your Price to park is " & Str(ChargeToPark))
        End If
        If Discount = True Then
            ChargeToPark -= ChargeToPark * DiscountAmount
            Console.WriteLine("your Discounted price is " & Str(ChargeToPark))
        End If
        ExitHour = ArrivalHour + TimeNeeded
        If ArrivalHour <= 16 And ExitHour > 16 And Discount = True Then
            ChargeToPark = (((16 - ArrivalHour) * ChargePerHour(DayNum)) * 0.1) + (((ExitHour - 16) * 2) * 0.5)
        Else
            ChargeToPark = ((16 - ArrivalHour) * ChargePerHour(DayNum)) + ((ExitHour - 16) * 2)
        End If
        Console.ReadKey()
    End Sub
End Module
