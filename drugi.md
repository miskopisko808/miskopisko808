package main;

import labis.cvorovi.CvorStabla;
import labis.exception.LabisException;
import labis.stabla.ABinarnoStablo;

public class BinarnoStablo extends ABinarnoStablo {

    public void infiksPomocna(CvorStabla koren) {
        if (koren == null) {
            return;
        }
        infiksPomocna(koren.levo);
        System.out.print(koren.podatak + " ");
        infiksPomocna(koren.desno);
    }

    public void infiksOriginal() throws LabisException {
        if (koren == null) {
            throw new LabisException();
        }
        infiksPomocna(koren);
    }

    public int brElemGlavna() throws LabisException{
        if (koren==null){
            throw new LabisException();
        }
        return brojElem(koren);
    }

    public int brojElem(CvorStabla koren){
        if(koren==null){
            return 0;
        }
        return 1 + brojElem(koren.levo) + brojElem(koren.desno);
    }

    public int zbir(CvorStabla koren){
        if (koren == null){
            return 0;
        }
        return koren.podatak + zbir(koren.levo)+zbir(koren.desno);
    }

    public double prosek(CvorStabla koren) throws LabisException {
        if (koren == null){
           throw new LabisException();
        }
        return (double) zbir(koren)/brojElem(koren);
    }


    public boolean sviCvorovi5Pom(CvorStabla koren){
        if (koren == null){
            return true;
        }
        return (koren.podatak == 5 &&sviCvorovi5Pom(koren.desno) && sviCvorovi5Pom(koren.levo));
    }

    public int proizvodNeparnihPom(CvorStabla koren){
        if(koren == null){
            return 1;
        }
        if (koren.podatak%2 == 1){
            return koren.podatak * proizvodNeparnihPom(koren.levo) * proizvodNeparnihPom(koren.desno);

        }
        return proizvodNeparnihPom(koren.levo)*proizvodNeparnihPom(koren.desno);
    }

    public int brCvorovaLevoDete() throws LabisException{
        if (koren==null){
            throw new LabisException();
        }
        return brojCvorovaLevoDetePom(koren);
    }


    public int brojCvorovaLevoDetePom(CvorStabla koren){
        if (koren == null){
            return 0;
        }
        if (koren.levo!=null){
            return 1 + brojCvorovaLevoDetePom(koren.levo) + brojCvorovaLevoDetePom(koren.desno);
        }
        // da se trazi zbir bio bi koren.podatak pa onda plus ostalo gore tamo
        return brojCvorovaLevoDetePom(koren.levo) + brojCvorovaLevoDetePom(koren.desno);
    }


    @Override
    public boolean daLiPostojiIsti(CvorStabla k, CvorStabla cvor) throws LabisException {
        if (koren == null){
            throw new LabisException();
        }
        if(cvor == null){
            throw new LabisException();
        }
        return postoji(cvor,koren);
    }


    public boolean postoji(CvorStabla cvor, CvorStabla koren){
        if (koren == null){
            return false;
        }
        if (koren == cvor){
            return true;
        }
        return postoji(cvor, koren.levo) || postoji(cvor, koren.desno);
    }

    public int brojElUIntervaluPom(CvorStabla koren, int dg, int gg){
        if (koren == null){
            return 0;
        }
        if (koren.podatak>dg && koren.podatak<gg){
            return 1 + brojElUIntervaluPom(koren.desno, dg, gg) + brojElUIntervaluPom(koren.levo, dg, gg);
        }
        return brojElUIntervaluPom(koren.desno,dg,gg) + brojElUIntervaluPom(koren.levo, dg, gg);
    }
    public int brojElUInt(int dg, int gg) throws LabisException{
        if (koren == null){
            throw new LabisException();
        }
        if (dg>=gg){
            throw new LabisException();
        }
        return brojElUIntervaluPom(koren, dg, gg);
    }

    public int brojNepListovaPom(CvorStabla koren){
        if (koren == null){
            return 0;
        }
        if(koren.levo == null || koren.desno == null && koren.podatak%2==1){
            return 1 + brojNepListovaPom(koren.desno) + brojNepListovaPom(koren.levo);
        }
        return brojNepListovaPom(koren.levo)+brojNepListovaPom(koren.desno);
    }


    public int zbirJednocifrenihPolulistova(CvorStabla koren){
        if (koren == null){
            return 0;
        }
        if (((koren.levo == null) != (koren.desno==null)) && koren.podatak%10 <10){
            return koren.podatak + zbirJednocifrenihPolulistova(koren.levo)+
                    zbirJednocifrenihPolulistova(koren.desno);
        }
        return zbirJednocifrenihPolulistova(koren.desno)+zbirJednocifrenihPolulistova(koren.levo);
    }

    public int proizvodCvVecihOdZbiraDece(CvorStabla koren){
        if (koren == null){
            return 1;
        }
        if (koren.levo!=null && koren.desno!=null && koren.levo.podatak + koren.desno.podatak < koren.podatak){
            return koren.podatak * proizvodCvVecihOdZbiraDece(koren.levo)
                    * proizvodCvVecihOdZbiraDece(koren.desno);
        }
        return proizvodCvVecihOdZbiraDece(koren.desno)*proizvodCvVecihOdZbiraDece(koren.levo);
    }

    public int brElemSaManjimDetetom(CvorStabla koren){
        if (koren == null || koren.levo==null || koren.desno==null){
            return 0;
        }
        if (koren.levo.podatak<=koren.podatak || koren.desno.podatak<= koren.podatak){
            return 1 + brElemSaManjimDetetom(koren.levo)+brElemSaManjimDetetom(koren.desno);
        }
        return brElemSaManjimDetetom(koren.levo)+brElemSaManjimDetetom(koren.desno);
    }

    public int max(CvorStabla koren){
        if (koren==null){
            return Integer.MIN_VALUE;
        }
        return Math.max(koren.podatak, Math.max(max(koren.levo), max(koren.desno)));
    }


    public int visina(CvorStabla koren){
        if (koren == null){
            return 0;
        }
        if (koren.levo==null && koren.desno == null){
            return 1;
        }
        return 1 + Math.max(visina(koren.desno), visina(koren.levo));
    }


}

