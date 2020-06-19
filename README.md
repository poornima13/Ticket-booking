# Ticket-booking
class movTick:
    m=0 ## BOOKING ID
    n=[10,10,10,10]  ## MAX TICKET
    DataBaseId=[]
    DataBaseTick=[]
    DataBaseMov=[]
    DataBaseUser=[]
   
    
    def __init__(self,USER_NAME):
            import time
            import smtplib
            import random
        
            self.mailID=USER_NAME
            Your_Order=[] 
            Food_cost=0
            Food_Flag=True
        
            my_movie=["1.GG:-","2.Dadk:-","3.RUSH:- ","4. KD100.:-"]
            TPrice=[120,100,100,300]
        
            my_food=["1.Mazaa:-","2.Vodka:-","3.Rum:-","4.Wiskey:-"]
            Price=[10,100,100,300]
        
            movieList=["Geetha Govindam movie","Dadak movie","RUSH movie","KD100 movie"]
            foodList=["Mazza","Vodka","Rum","Wiskey"]
        
        
            print("{}".format(list(zip(my_movie,TPrice))))
            sel=int(input ('Select the MOVIE: '))
            num=int(input ('No. of SEATS'))
        
            if(num>movTick.n[sel-1]):
            
                print("BOOKING FAILED(HOUSEFULL)")
            
            else:
                TicketPrice=num*TPrice[sel-1]
                print('Total Cost Of TICKETS : {}'.format(TicketPrice))
                Your_Order.append([movieList[sel-1],num])
            
                p=input("NEED FOOD?(Y/N): ") 
                while(p=='Y'):
                    print("FOOD LIST {}".format(list(zip(my_food,Price))))
                    f=int(input("Select Order:"))
                    f=f-1
                    Fcost=Price[f]
                    q=int(input("Quanity:"))
                    Food_cost+=q*Fcost
                
                    print("Food Cost: {}".format(Food_cost))
                    Your_Order.append([foodList[f],q])
                
                    Re_order=input("Want some More?(Y?N):")
                    if(Re_order!='Y'):
                        break
                Confirm=input("Do yoU want to Confirm Tickets:")
                if(Confirm=='Y'):
                    p=int(random.randint(999,9999))
                    TotalCost=Food_cost+TicketPrice
                    msg="Subject:OTP GENERATION\nHey User,\nYour few steps away to book " +movieList[sel-1] +"movie\nThe total cost to be paid is: "+str(TotalCost)+"\n\n\nOTP:-"+str(p)
                    
    
                    server=smtplib.SMTP('smtp.gmail.com',587)
                    server.ehlo()
                    server.starttls()
                    server.ehlo()
                    server.login('raspberryp087@gmail.com','Raspberry@123')
                    
                    server.sendmail('raspberryp087@gmail.com',self.mailID,msg)
                    
                    
                    print("OTP sent to ur mailID{}".format(self.mailID))
                    time.sleep(5)
                    server.close()
                    OTP=int(input("ENTER THE OTP: "))
                    if(p==OTP):
                        print("OTP Succesfull")
                        movTick.m=movTick.m+1 ##id
                        movTick.n[sel-1]-=num ##DEC.. THE MAX TICKETS
                        
                        movTick.DataBaseId.append(movTick.m)
                        movTick.DataBaseTick.append(num)
                        movTick.DataBaseMov.append(sel)
                        movTick.DataBaseUser.append(self.mailID)
                        print("Tickets Has be booked Booking Id:{}".format(movTick.m))
                        print("Total cost={}".format(Food_cost+TicketPrice))
                        print("Your FINAL ORDER:")
                        print(Your_Order)
                        print(movTick.n)
                        print("ID" ,movTick.m)
                    else:
                        print("OTP authentication FAILED!")
                else:
                    print("BOOKING FAILED!!")
    def Cancel(self,USER_id):
        import time
        import smtplib
        import random
        self.Userid=USER_id
        CConfirm=input("Do yoU want to CANCEL YOUR TICKET?(Y/N?):")
        if(CConfirm=='Y'):
            Send_mail=movTick.DataBaseUser[self.Userid-1]
            p1=int(random.randint(999,9999))
            msg1="Subject:Cancellation OTP GENERATION\nHey User,\nYour few steps away to cancel your booking "+"\nOTP is :-"+str(p1)
            server=smtplib.SMTP('smtp.gmail.com',587)
            server.ehlo()
            server.starttls()
            server.ehlo()
            server.login('raspberryp087@gmail.com','Raspberry@123')
            server.sendmail('raspberryp087@gmail.com',Send_mail,msg1)
            print("OTP sent to ur mailID{}".format(self.mailID))
            time.sleep(5)
            server.close()
            OTP1=int(input("ENTER THE OTP: "))
            if(p1==OTP1):
                print("OTP Succesfull")
                movTick.n[movTick.DataBaseMov[self.Userid-1]-1]+=movTick.DataBaseTick[self.Userid-1]
                print(movTick.n)
                print("Cancellation Succesfull")
            else:
                print("Cancellation Failed!!!")
        else:
            print("Cancellation Failed!!!")
                
                
        v=movTick('r.pav96@gmail.com')
         print("ID" ,movTick.m)
         v.Cancel(1)
         movTick.n
          movieList=["Geetha Govindam movie","Dadak movie","RUSH movie","KD100 movie"]
          import random
           random.ra
