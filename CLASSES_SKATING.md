```.p
class BaseTypeScoring:
    def __init__(self,jump:str,sequence:str,spin:str,lift:str,flip:str):
        self.jump=jump
        self.sequence=sequence
        self.spin=spin
        self.lift=lift
        self.flip=flip
        self.jumpscore=0
        self.sequencescore=0
        self.spinscore = 0
        self.liftscore = 0
        self.flipscore = 0
    def jumpscoring(self):
        if self.jump=='axel':
            self.jumpscore+=8
        elif self.jump=='Lutz':
            self.jumpscore+=5.9
        elif self.jump=='Salchow':
            self.jumpscore+=9.7
        return self.jumpscore

    def sequencescoring(self):
        if self.sequence=='success':
            self.sequencescore+=5
        else:
            self.sequencescore+=1.5
        return  self.sequencescore
    def spinscoring(self):
        if self.spin=='long':
            self.spinscore+=4
        else:
            self.spinscore+=2
        return self.spinscore
    def liftscoring(self):
        if self.lift=='success':
            self.liftscore+=8.5
        else:
            self.liftscore+=3
        return self.liftscore
    def flipscoring(self):
        if self.flip=='success':
            self.flipscore+=5
        else:
            self.flipscore+=1
        return self.flipscore

class TotalScore(BaseTypeScoring):
    def __init__(self,jumpn:int,sequencen:int,spinn:int,liftn:int,flipn:int,total:int):
        self.jumpn=jumpn
        self.sequencen=sequencen
        self.spinn=spinn
        self.liftn=liftn
        self.flipn:flipn
        self.total=total

    def jumpscoref(self):
        self.total=(self.jumpn * self.jump)
        return self.total
    def sequencescoref(self):
        self.total=(self.sequencen * self.sequence)
        return self.total
    def spinscoref(self):
        self.total=(self.spinn * self.spin)
        return self.total
    def liftscoref(self):
        self.total=(self.liftn * self.lift)
        return self.total
    def flipscoref(self):
        self.total=(self.flipn * self.flip)
        return self.total
    def totalscore(self):
        self.total=(self.jumpn * self.jump)+(self.sequencen * self.sequence)+(self.spinn * self.spin)+(self.liftn * self.lift)+(self.flipn * self.flip)
        return self.total
    


```
