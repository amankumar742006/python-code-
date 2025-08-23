 # python-code-1-bus-ticket-
projrct on python bus ticket using oops

class BusTicket:
    def __init__(self, name, phone, passengers, seat_type, destination):
        self.name = name
        self.phone = phone
        self.passengers = passengers
        self.seat_type = seat_type
        self.destination = destination
        self.bus_no = "ABC1234"   # Fixed bus number
        self.base_fare = {
            "Dehradun": 500,
            "Jaipur": 600,
            "Amritsar": 800,
            "Indore": 1000
        }
        self.gst_rate = 0.18

    def calculate_bill(self):
        fare = self.base_fare[self.destination] * self.passengers
        seat_charge = (100 if self.seat_type.lower() == "window" else 50) * self.passengers
        total = fare + seat_charge
        gst = total * self.gst_rate
        final_amount = total + gst
        return fare, seat_charge, gst, final_amount

    def show_bill(self):
        fare, seat_charge, gst, final_amount = self.calculate_bill()
        print("\n*** WELCOME TO ABC BUS SERVICE ***")
        print("----------- BUS TICKET BILL -----------")
        print(f"Passenger Name   : {self.name}")
        print(f"Phone No.        : {self.phone}")
        print(f"No. of Passengers: {self.passengers}")
        print(f"Seat Type        : {self.seat_type}")
        print(f"Destination      : {self.destination}")
        print(f"Base Fare        : ₹{fare}")
        print(f"Seat Charge      : ₹{seat_charge}")
        print(f"GST (18%)        : ₹{gst:.2f}")
        print(f"Total Amount     : ₹{final_amount:.2f}")
        print(f"Bus Number       : {self.bus_no}")
        print("--------------------------------------")
        print("Have a safe journey !!")


# --- Main Program ---
name = input("Enter passenger name: ")
phone = input("Enter phone number: ")
passengers = int(input("Enter number of passengers: "))
seat_type = input("Choose seat (Window/Non Window): ")
print("Destinations: Dehradun, Jaipur, Amritsar, Indore")
destination = input("Enter your destination: ")

ticket = BusTicket(name, phone, passengers, seat_type, destination)
ticket.show_bill()
