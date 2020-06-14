# myCheatSheet
My CheatSheet

# How can I print a float with thousands separators?
https://stackoverflow.com/questions/13082620/how-can-i-print-a-float-with-thousands-separators


import re
def sep(s, thou=",", dec=".", roundTo=None):
    if roundTo == None:
        integer, decimal = str(s).split(".")
        integer = re.sub(r"\B(?=(?:\d{3})+$)", thou, integer)
        return integer + dec + decimal
    else:
        newS = str(round(s,roundTo))
        integer, decimal = newS.split(".")
        integer = re.sub(r"\B(?=(?:\d{3})+$)", thou, integer)
        return integer + dec + decimal

s = float("5255918.87898331")
sep(s, roundTo=2)
