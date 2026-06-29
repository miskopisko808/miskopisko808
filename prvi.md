//JSLista
package main;

import labis.cvorovi.CvorJSListe;
import labis.exception.LabisException;
import labis.liste.AJSLista;

public class JSLista extends AJSLista {


    public void ispisiListu () throws LabisException {

        if (prvi == null){
            throw new LabisException("Lista je prazna");
        }
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            System.out.print(tekuci.podatak + " ");
            tekuci = tekuci.sledeci;
        }
        System.out.println();
    }

    public void dodajNaPocetak(int element){

        CvorJSListe cvor = new CvorJSListe(element, prvi);
        prvi = cvor;

    }

    public void dodajNaKraj(int element){

        if(prvi == null){
            CvorJSListe cvor = new CvorJSListe(element, prvi);
            prvi = cvor;
        }

        CvorJSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        CvorJSListe cvor = new CvorJSListe(element, null);
        tekuci.sledeci = cvor;
    }

    public boolean postoji(int element) throws LabisException {

        if (prvi == null){
            throw new LabisException("Lista je prazna");
        }

        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if(tekuci.podatak == element){
                return true;
            }
            tekuci = tekuci.sledeci;
        }
        return false;
    }


    public boolean postojiCvor(CvorJSListe cvor) throws LabisException {

        if (prvi == null){
            throw new LabisException();
        }

        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if (tekuci == cvor){
                return true;
            }
            tekuci = tekuci.sledeci;
        }

        return false;
    }


    public int brojNegativnih() throws LabisException{

        if (prvi == null){
            throw new LabisException("Prazna");
        }
        int brojac = 0;
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if (tekuci.podatak < 0){
                brojac++;
            }
            tekuci = tekuci.sledeci;
        }
        return brojac;
    }

    public int zbirElNaParnimMestima() throws LabisException{

        if (prvi == null){
            throw new LabisException();
        }

       int zbir = 0;
       int indeks = 1;
       CvorJSListe tekuci = prvi;
       while(tekuci!=null){
           if (indeks%2==0){
               zbir = zbir + tekuci.podatak;
           }
           indeks++;
           tekuci = tekuci.sledeci;
       }
       return zbir;
    }


    public int proizvodDvocifrenihPozitivnih() throws LabisException{
        if(prvi == null){
            throw new LabisException();
        }

        int proizvod = 1;

        CvorJSListe tekuci = prvi;
        while (tekuci!=null){
            if (tekuci.podatak >=10 && tekuci.podatak <=99){
                proizvod*=tekuci.podatak;
            }
            tekuci = tekuci.sledeci;
        }
        if(proizvod == 1){
            throw new LabisException();
        }
        return proizvod;

    }

    public int maxElement() throws LabisException{
        if(prvi == null){
            throw new LabisException();
        }
        int max = Integer.MIN_VALUE;
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if (tekuci.podatak>max){
                max = tekuci.podatak;
            }
            tekuci = tekuci.sledeci;
        }
        return max;
    }

    public int najmanjiEl() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        int min = Integer.MAX_VALUE;
        while(tekuci!=null){
            if (tekuci.podatak<min){
                min = tekuci.podatak;
            }
            tekuci = tekuci.sledeci;
        }
        return min;
    }

    public CvorJSListe najveciCvor() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorJSListe maxCvor = prvi;
        CvorJSListe tekuci = prvi;
        int max = Integer.MIN_VALUE;

        while(tekuci!=null){
            if (tekuci.podatak>max){
                max = tekuci.podatak;
                maxCvor = tekuci;
            }
            tekuci = tekuci.sledeci;
        }
        return maxCvor;
    }

    public void izbaciPrvi() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        prvi = prvi.sledeci;
    }

    public void izbaciPoslednji() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        if (prvi.sledeci==null){
            prvi = null;
            return;
        }

        CvorJSListe tekuci = prvi;
        while (tekuci.sledeci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        tekuci.sledeci = null;
    }


    public void izbaciPretposlednji() throws LabisException{

        if (prvi == null || prvi.sledeci ==null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        CvorJSListe prethodni = tekuci;
        while(tekuci.sledeci.sledeci!=null){
            prethodni = tekuci;
            tekuci = tekuci.sledeci;
        }
        prethodni.sledeci = tekuci.sledeci;

    }

    public void izbaciCvor (CvorJSListe cvor) throws LabisException{

        if (prvi == null){
            throw new LabisException();
        }
        if (prvi == cvor){
            prvi = prvi.sledeci;
            return;
        }

        CvorJSListe tekuci = prvi;
        CvorJSListe prethodni = null;

        while(tekuci.sledeci!=null){
            if (tekuci == cvor){
                prethodni.sledeci = tekuci.sledeci;
                return;
            }
            prethodni = tekuci;
            tekuci = tekuci.sledeci;
        }

        if (tekuci == cvor){
            prethodni.sledeci = null;
            return;
        }
        throw new LabisException();
    }

    public int brojElemenata(){
        int brojac = 0;
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            brojac++;
            tekuci = tekuci.sledeci;
        }
        return brojac;
    }


   public void ubaciNaPoziciju(int pozicija, int broj) throws LabisException{

       CvorJSListe cvor = new CvorJSListe(broj, null);

        if (pozicija < 0 || pozicija>brojElemenata()){
            throw new LabisException();
        }
        if (pozicija == 0){
            cvor.sledeci = prvi;
            prvi = cvor;
            return;
        }

        CvorJSListe tekuci = prvi;
        CvorJSListe prethodni = null;

        for (int i = 0; i < pozicija; i++){
            prethodni = tekuci;
            tekuci = tekuci.sledeci;
        }
        cvor.sledeci = tekuci;
        prethodni.sledeci = cvor;

   }

    public void izbaciSaPozicije(int pozicija)throws LabisException{

        if (pozicija<0 || pozicija>brojElemenata()){
            throw new LabisException();
        }
        if (pozicija == 0){
            prvi = prvi.sledeci;
            return;
        }

        CvorJSListe tekuci = prvi;
        for (int i = 0; i < pozicija-1; i++){
            tekuci = tekuci.sledeci;
        }
        tekuci.sledeci = tekuci.sledeci.sledeci;

    }

    //na pretposl mesto ubacuje elem koji je duplo veci od prvog elem

    public void ubaciDuploVeci() throws LabisException{
        CvorJSListe cvor = new CvorJSListe(prvi.podatak*2, null);

        if (prvi == null){
            throw new LabisException();
        }
        if (prvi.sledeci==null){
            cvor.sledeci = prvi;
            prvi = cvor;
            return;
        }

        CvorJSListe tekuci = prvi;

       while(tekuci.sledeci.sledeci!=null){
           tekuci = tekuci.sledeci;
       }
       cvor.sledeci = tekuci;
       tekuci.sledeci = cvor;
    }

    public void ubaciPozPosleNeg() throws LabisException{

        if (prvi == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if (tekuci.podatak < 0){
                tekuci.sledeci = new CvorJSListe(tekuci.podatak*(-1), tekuci.sledeci);
            }
            tekuci = tekuci.sledeci;
        }

    }

    // koliko se puta ponovio najcesci el
     public int brojPojavljivanja(int broj){
        int brojac = 0;
        CvorJSListe tekuci = prvi;
        while(tekuci!=null){
            if (tekuci.podatak == broj){
                brojac++;
            }
            tekuci = tekuci.sledeci;
        }
        return brojac;
     }

     public int najcescePonavljan() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        int max = Integer.MIN_VALUE;

        while(tekuci!=null){
            if (brojPojavljivanja(tekuci.podatak) > max){
                max = brojPojavljivanja(tekuci.podatak);
            }
            tekuci = tekuci.sledeci;
        }
        return max;
     }

     //funkcija koja broji koliko ima parova elem ciji je zbir k

    public int brojParova(int k) throws LabisException{
        if(prvi == null || prvi.sledeci == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        CvorJSListe pomocni = prvi;
        int brojac = 0;

        while(tekuci.sledeci!=null){
            pomocni = tekuci.sledeci;
            while(pomocni!=null){
                if (pomocni.podatak+tekuci.podatak==k){
                    brojac++;
                }
                pomocni = pomocni.sledeci;
            }
            tekuci = tekuci.sledeci;
        }
        return brojac;
    }

    //ako su susedni parovi
    public int brojSusednihSaSumom(int k) throws LabisException{
        int brojac = 0;
        CvorJSListe tekuci = prvi;
        if (prvi == null || prvi.sledeci == null){
            throw new LabisException();
        }
        while(tekuci.sledeci!=null){
            if (tekuci.podatak + tekuci.sledeci.podatak == k){
                brojac++;
            }
            tekuci = tekuci.sledeci;
        }

        return brojac;
    }

    //ubacuje p posle prvog elem manjeg od p, ako ne onda na kraj

    public void ubaciP(int p) throws LabisException{

        if (prvi == null){
            prvi = new CvorJSListe(p,prvi);
            return;
        }
        CvorJSListe tekuci = prvi;
        CvorJSListe cvor = new CvorJSListe(p, null);
        while(tekuci.sledeci!=null){
            if(tekuci.podatak<p){
                cvor.sledeci = tekuci.sledeci;
                tekuci.sledeci = cvor;
                return;
            }
            tekuci = tekuci.sledeci;
        }
        tekuci.sledeci = cvor;

    }

    public void dodajCvorNaPoc(CvorJSListe cvor){
        cvor.sledeci = prvi;
        prvi = cvor;
    }

    public void invertujListu() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        if (prvi.sledeci == null){
            return;
        }

        CvorJSListe tekuci = prvi;
        CvorJSListe pomocni;

        while(tekuci!=null){
            pomocni = tekuci;
            tekuci = tekuci.sledeci;
            izbaciCvor(pomocni);
            dodajCvorNaPoc(pomocni);
        }
    }

    public int zbirNajvecaTri() throws LabisException{

        if (prvi == null || prvi.sledeci == null || prvi.sledeci.sledeci ==null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        int e1 = Integer.MIN_VALUE;
        int e2 = Integer.MIN_VALUE;
        int e3 = Integer.MIN_VALUE;

        while(tekuci!=null){
            if (tekuci.podatak >= e1){
                e3 = e2;
                e2 = e1;
                e1 = tekuci.podatak;
            }
            else if (tekuci.podatak>=e2){
                e2 = e1;
                e1 = tekuci.podatak;
            }
            else if (tekuci.podatak>=e3){
                e3 = tekuci.podatak;
            }
            tekuci = tekuci.sledeci;
        }
        return e1+e2+e3;
    }

    //preskace m elemenata pa ubacuje n elemenata

    public void preskociMIzbaciN(int m, int n) throws LabisException{

        if (prvi==null){throw new LabisException();
        }

        CvorJSListe tekuci = prvi;
        CvorJSListe pomocni = tekuci;
        while(tekuci!=null){
            for (int i = 0; i < m && tekuci!=null; i++){
                tekuci = tekuci.sledeci;
            }
            for (int j = 0; j < n && tekuci!=null; j++){
                pomocni = tekuci;
                tekuci = tekuci.sledeci;
                izbaciCvor(pomocni);
            }
        }
    }

    //ubacuje broj na n tu poziciju od kraja liste

    public void ubaciNaNtuPoz(int broj, int n) throws LabisException{
        if (n == brojElemenata()){
            prvi = new CvorJSListe(broj, prvi);
        }
        if (n<0 || n>=brojElemenata()){
            throw new LabisException();
        }

        CvorJSListe spori = prvi;
        CvorJSListe brzi = prvi;

        for (int i = 0; i <=n; i++){
            brzi = brzi.sledeci;
        }
        while(brzi!=null){
            brzi = brzi.sledeci;
            spori = spori.sledeci;
        }
        spori.sledeci = new CvorJSListe(broj,spori.sledeci);
    }


    public int dnevneTemp(CvorJSListe prvi1, CvorJSListe prvi2) throws LabisException {
        if (prvi1 == null || prvi2 == null){
            throw new LabisException();
        }
       int maxRazlika = 0;
       while(prvi1!=null && prvi2!=null){
           int razlika = Math.abs(prvi1.podatak-prvi2.podatak);
           if (razlika > maxRazlika){
               maxRazlika = razlika;
           }
           prvi1 = prvi1.sledeci;
           prvi2 = prvi2.sledeci;
       }
        return maxRazlika;
    }

//izbacuje cvor koji se nalazi pre prvog cvora koji ima sadrzaj manji od prosecne vr elem
// u listi i vraca vr izbacenog cvora

    public int metoda8(int podatak) throws LabisException {

        if (prvi == null || prvi.sledeci == null) {
            throw new LabisException();
        }

        int suma = 0;
        CvorJSListe pomocni = prvi;

        while (pomocni != null) {
            suma += pomocni.podatak;
            pomocni = pomocni.sledeci;
        }

        double prosek = (double) suma / brojElemenata();

        CvorJSListe prethodni = prvi;
        CvorJSListe tekuci = prvi.sledeci;

        if (prvi.podatak < prosek) {
            throw new LabisException();
        }

        while (tekuci != null) {
            if (tekuci.podatak < prosek) {
                int vr = prethodni.podatak;
                // brisanje prethodnog cvora
                if (prethodni == prvi) {
                    prvi = tekuci;
                } else {
                    CvorJSListe p = prvi;

                    while (p.sledeci != prethodni) {
                        p = p.sledeci;
                    }

                    p.sledeci = tekuci;
                }
                return vr;
            }
            prethodni = tekuci;
            tekuci = tekuci.sledeci;
        }
        return -1;
    }






}





//DS lista
package main;

import labis.cvorovi.CvorDSListe;
import labis.exception.LabisException;
import labis.liste.ADSLista;

public class DSLista extends ADSLista {

    public void ispisiListu() throws LabisException{

        if (prvi == null){
            throw new LabisException("prazna");
        }

        CvorDSListe tekuci = prvi;
        while(tekuci!=null){
            System.out.print(tekuci.podatak+" ");
            tekuci = tekuci.sledeci;
        }
        System.out.println();
    }


    public void ispisUnazad() throws LabisException{

        if (prvi == null){
            throw new LabisException();
        }
        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        while (tekuci!=null){
            System.out.print(tekuci.podatak+" ");
            tekuci = tekuci.prethodni;
        }
        System.out.println();
    }


    public void dodajNaKraj(int broj) throws LabisException{

        if (prvi == null){
            prvi = new CvorDSListe(broj,null,null);
            return;
        }

        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        tekuci.sledeci = new CvorDSListe(broj, tekuci, null);


    }

    public void dodajNaPocetak(int broj){
        if (prvi == null){
            prvi = new CvorDSListe(broj,null,null);
            return;
        }
        CvorDSListe cvor = new CvorDSListe(broj,null,prvi);
        prvi.prethodni = cvor;
        cvor.sledeci = prvi;
        prvi = cvor;
    }


    public void popuniListu() throws LabisException{

        if(prvi==null || prvi.sledeci==null){
            throw new LabisException();
        }

        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            if(tekuci.podatak-tekuci.sledeci.podatak!=-1){
                CvorDSListe cvor = new CvorDSListe(tekuci.podatak+1, tekuci, tekuci.sledeci);
                tekuci.sledeci.prethodni = cvor;
                tekuci.sledeci = cvor;
            }
            tekuci = tekuci.sledeci;
        }
    }

    public void izbaciCvor (CvorDSListe cvor) throws LabisException{

        if(prvi == null){
            throw new LabisException();
        }
        if(prvi.sledeci==null && prvi == cvor){
            prvi = null;
            return;
        }
        if(prvi == cvor){
            prvi = prvi.sledeci;
            prvi.prethodni = null;
            return;
        }


        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            if (tekuci == cvor){
                tekuci.prethodni.sledeci = tekuci.sledeci;
                tekuci.sledeci.prethodni = tekuci.prethodni;
                return;
            }
            tekuci = tekuci.sledeci;
        }
        if (tekuci == cvor){
            tekuci.prethodni.sledeci = null;
            return;
        }
        throw new LabisException();
    }

    public CvorDSListe najmanjiCvor() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorDSListe tekuci = prvi;
        CvorDSListe min = prvi;
        while(tekuci!=null){
            if (tekuci.podatak<min.podatak){
                min = tekuci;
            }
            tekuci = tekuci.sledeci;
        }
        return min;
    }

    public void dodajCvorNaPocetak(CvorDSListe cvor){
        cvor.sledeci = prvi;
        cvor.prethodni = null;
        if(prvi != null){
            prvi.prethodni = cvor;
        }
        prvi = cvor;
    }

    public void minNaPocetak() throws LabisException{

        CvorDSListe min = najmanjiCvor();
        if (prvi == null){
            throw new LabisException();
        }
        if(prvi == min){
            return;
        }

        min.prethodni.sledeci = min.sledeci;
        if(min.sledeci!=null){
            min.sledeci.prethodni = min.prethodni;
        }

        min.prethodni = null;
        min.sledeci = prvi;
        prvi.prethodni = min;
        prvi = min;
    }

    public void dodajNaPretposlednjeMesto(int broj) throws LabisException{
        if (prvi == null ){
            throw new LabisException();
        }
        if(prvi.sledeci == null){
            prvi = new CvorDSListe(broj,null,prvi);
            return;
        }

        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        CvorDSListe cvor = new CvorDSListe(broj,tekuci, tekuci.sledeci);
        tekuci.sledeci.prethodni = cvor;
        tekuci.sledeci = cvor;

    }

    public void ubaciPrePretposlednjeg(int broj) throws LabisException{

        if (prvi == null || prvi.sledeci==null){
            throw new LabisException();
        }

        if (prvi.sledeci.sledeci==null) {
            CvorDSListe cvor = new CvorDSListe(broj, null, prvi);
            prvi.prethodni = cvor;
            cvor.sledeci = prvi;
            prvi = cvor;
            return;
        }

        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci.sledeci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        CvorDSListe cvor = new CvorDSListe(broj,tekuci, tekuci.sledeci);
        tekuci.sledeci.prethodni = cvor;
        tekuci.sledeci = cvor;
    }


    public void izbaciDrugiITreci() throws LabisException{

        if (prvi==null || prvi.sledeci==null || prvi.sledeci.sledeci==null){
            throw new LabisException();
        }

        CvorDSListe tekuci = prvi.sledeci.sledeci.sledeci;
        prvi.sledeci = tekuci;
        if(tekuci!=null){
            tekuci.prethodni = prvi;
        }

    }

    public boolean postoji(CvorDSListe cvor, CvorDSListe prvi) throws LabisException{
        if (prvi == null){
            return false;
        }

        CvorDSListe tekuci = prvi;
        while(tekuci!=null){
            if(tekuci==cvor){
                return true;
            }
            tekuci = tekuci.sledeci;
        }
        return false;
    }

    public CvorDSListe vratiCvorUKomeSeSpajaju(CvorDSListe prvi1, CvorDSListe prvi2) throws LabisException{
        if(prvi1==null || prvi2 ==null){
            throw new LabisException();
        }

        CvorDSListe tekuci1 = prvi1;
        while(tekuci1!=null){
            if(postoji(tekuci1,prvi2)){
                return tekuci1;
            }
            tekuci1 = tekuci1.sledeci;
        }

        return null;
    }

    public int brojElem(CvorDSListe prvi){
        int brojac = 0;
        CvorDSListe tekuci = prvi;
        while(tekuci!=null){
            brojac++;
            tekuci = tekuci.sledeci;
        }
        return brojac;
    }

    public int listaUBroj(CvorDSListe prvi) throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        int broj = 0;
        int koef = (int) Math.pow(10, brojElem(prvi)-1);
        CvorDSListe tekuci = prvi;
        while(tekuci!=null){
            broj+=tekuci.podatak*koef;
            tekuci = tekuci.sledeci;
            koef/=10;
        }
        return broj;
    }


    public CvorDSListe saberiDveListe(CvorDSListe prvi1, CvorDSListe prvi2) throws LabisException{
        if (prvi1==null || prvi2 == null){
            throw new LabisException();
        }

        int broj1 = listaUBroj(prvi1);
        int broj2 = listaUBroj(prvi2);
        int zbir = broj1+broj2;

        DSLista lista = new DSLista();
        while(zbir>0){
            int j = zbir%10;
            lista.dodajNaPocetak(j);
            zbir/=10;
        }
        return lista.prvi;
    }

    public int vratiPoslednji() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorDSListe tekuci = prvi;
        while(tekuci.sledeci!=null){
            tekuci = tekuci.sledeci;
        }
        return tekuci.podatak;
    }

    public void izbaciNeparneManjeOdPoslednjeg() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }

        int poslednji = vratiPoslednji();
        CvorDSListe tekuci = prvi;
        while(tekuci!=null){
            if(tekuci.podatak%2==1 && tekuci.podatak<poslednji){
                izbaciCvor(tekuci);
            }
            tekuci = tekuci.sledeci;
        }
    }



}


//ciklicna js
package main;

import labis.cvorovi.CvorJSListe;
import labis.exception.LabisException;
import labis.liste.AJSLista;

import javax.swing.text.html.HTMLEditorKit;

public class CiklicnaJSLista extends AJSLista {

    public void ispisi() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        do{
            System.out.print(tekuci.podatak + " ");
            tekuci = tekuci.sledeci;
        }while(tekuci!=prvi);
        System.out.println();
    }

    public void dodajNaKraj(int broj){
        CvorJSListe cvor = new CvorJSListe(broj, null);
        CvorJSListe tekuci = prvi;
        if(prvi == null){
            prvi = cvor;
            cvor.sledeci = prvi;
            return;
        }
        do{
            tekuci = tekuci.sledeci;
        }while(tekuci.sledeci!=prvi);
        tekuci.sledeci = cvor;
        cvor.sledeci = prvi;
    }

    public void dodajNaPocetak(int broj){
        CvorJSListe cvor = new CvorJSListe(broj,null);
        CvorJSListe tekuci = prvi;

        if(prvi == null){
            prvi = cvor;
            cvor.sledeci = prvi;
            return;
        }

        do{
            tekuci = tekuci.sledeci;
        }while(tekuci.sledeci!=prvi);
        tekuci.sledeci = cvor;
        cvor.sledeci = prvi;
        prvi = cvor;
    }

    public void ubaciIzmedju2Neg(int broj) throws LabisException{
        CvorJSListe tekuci = prvi;

        if(prvi == null){
            throw new LabisException();
        }

        do{
            if(tekuci.podatak<0 && tekuci.sledeci.podatak<0){
                CvorJSListe cvor = new CvorJSListe(broj, tekuci.sledeci);
                tekuci.sledeci = cvor;
                //cvor.sledeci = tekuci.sledeci;
            }
            tekuci = tekuci.sledeci;
        }while(tekuci!=prvi);
    }

    public int brojElemenata(){
        if (prvi == null){
            return 0;
        }
        int brojac = 0;

        CvorJSListe tekuci = prvi;
        do{
            brojac++;
            tekuci = tekuci.sledeci;
        } while(tekuci!=prvi);

        return brojac;
    }

    public int uporediDveListe(CiklicnaJSLista l1, CiklicnaJSLista l2){
        return l1.brojElemenata() - l2.brojElemenata();
    }

    //moze i da se stavi za brojElemenata(CvorJSListe prvi)
    // i posle uporediDveListe(CvorJSListe prvi1, CvorJSListe prvi2)

    public void izbaciCvor(CvorJSListe cvor) throws LabisException{

        CvorJSListe tekuci = prvi;
        CvorJSListe prethodni = prvi;

        if(prvi == null){
            throw new LabisException();
        }

        if(prvi==cvor && prvi.sledeci==prvi){
            prvi = null;
            return;
        }

        if (prvi == cvor){
            do{
                tekuci = tekuci.sledeci;
            }while(tekuci.sledeci!=prvi);
            prvi = prvi.sledeci;
            tekuci.sledeci = prvi;
            return;
        }


        do{
            if(tekuci == cvor){
                prethodni.sledeci = tekuci.sledeci;
                return;
            }
            prethodni = tekuci;
            tekuci = tekuci.sledeci;
        }while(tekuci.sledeci!=prvi);

        if(tekuci==cvor){
            prethodni.sledeci = prvi;
            return;
        }
        throw new LabisException();

    }


    public int vratiDrugiNajveciSort() throws LabisException{

        if(prvi == null || prvi.sledeci==null){
            throw new LabisException();
        }

        if(prvi.sledeci.sledeci == prvi){
            return prvi.podatak;
        }

        CvorJSListe tekuci = prvi;
        do{
            tekuci = tekuci.sledeci;
        }while(tekuci.sledeci.sledeci!=prvi);

        return tekuci.podatak;
    }

    public int vratiDrugiNajveciNesort() throws LabisException{

        if(prvi == null || prvi.sledeci == null){
            throw new LabisException();
        }
        CvorJSListe tekuci = prvi;
        int max1 = Integer.MIN_VALUE;
        int max2 = Integer.MIN_VALUE;

        do{
            if(tekuci.podatak>max1){
                max2 = max1;
                max1 = tekuci.podatak;
            }
            else if(tekuci.podatak>max2){
                max2 = tekuci.podatak;
            }
            tekuci = tekuci.sledeci;
        }while(tekuci!=prvi);
        return max2;

    }

    public CvorJSListe vrati2NajvNesort() throws LabisException{
        if (prvi == null || prvi.sledeci == null){
            throw new LabisException();
        }

        CvorJSListe tekuci = prvi;
        CvorJSListe cvor1 = null;
        CvorJSListe cvor2 = null;
        int max1 = Integer.MIN_VALUE;
        int max2 = Integer.MIN_VALUE;

        do{

            if(tekuci.podatak>max1){
                max2 = max1;
                cvor2 = cvor1;
                max1 = tekuci.podatak;
                cvor1 = tekuci;
            }

            else if(tekuci.podatak>max2){
                max2 = tekuci.podatak;
                cvor2 = tekuci;
            }
            tekuci = tekuci.sledeci;

        }while(tekuci!=prvi);
        return cvor2;


    }


}



//ciklicna ds

package main;

import labis.cvorovi.CvorDSListe;
import labis.exception.LabisException;
import labis.liste.ADSLista;

public class CiklicnaDSLista extends ADSLista {

    public void ispisi() throws LabisException{
        if(prvi == null){
            throw new LabisException();
        }
        CvorDSListe tekuci = prvi;
        do{
            System.out.print(tekuci.podatak+ " ");
            tekuci = tekuci.sledeci;
        }while(tekuci!=prvi);
        System.out.println();

    }

    public void ispisUnazad() throws LabisException{
        if (prvi == null){
            throw new LabisException();
        }
        CvorDSListe tekuci = prvi;
        do{
            tekuci = tekuci.sledeci;
        }while(tekuci.sledeci!=prvi);

        do{
            System.out.print(tekuci.podatak + " ");
            tekuci = tekuci.prethodni;
        }while(tekuci!=prvi.prethodni);
        System.out.println();
    }

    public void dodajNaKraj(int broj){

        if (prvi == null){
            CvorDSListe cvor = new CvorDSListe(broj,null,null);
            prvi = cvor;
            cvor.sledeci = cvor;
            cvor.prethodni = cvor;
            return;
        }

        CvorDSListe tekuci = prvi.prethodni;
        CvorDSListe cvor = new CvorDSListe(broj,tekuci,prvi);
        tekuci.sledeci = cvor;
        cvor.prethodni = cvor;
    }

    public void dodajNaPocetak(int broj) {

        if (prvi==null){
            CvorDSListe cvor = new CvorDSListe(broj, null,null);
            prvi = cvor;
            cvor.sledeci = cvor;
            cvor.prethodni = cvor;
            return;
        }

        CvorDSListe cvor = new CvorDSListe(broj,prvi.prethodni, prvi);
        prvi.prethodni.sledeci = cvor;
        prvi.prethodni = cvor;
        prvi = cvor;

    }

    public void izbaciCvor(CvorDSListe cvor) throws LabisException{

        if(prvi == null){
            throw new LabisException();
        }
        if(prvi == cvor && prvi.sledeci == prvi){
            prvi = null;
            return;
        }

        if(prvi == cvor){
            prvi.prethodni.sledeci = prvi.sledeci;
            prvi.sledeci.prethodni = prvi.prethodni;
            prvi = prvi.sledeci;
            return;
        }


        CvorDSListe tekuci = prvi;
        do{
            if(tekuci == cvor){
                tekuci.sledeci.prethodni = tekuci.prethodni;
                tekuci.prethodni.sledeci = tekuci.sledeci;
                return;
            }

            tekuci = tekuci.sledeci;
        }
        while(tekuci!=prvi);
    }


}



//niz

package main;

import labis.cvorovi.CvorJSListe;
import labis.exception.LabisException;
import labis.niz.ANiz;

import javax.swing.text.LayoutQueue;

public class Niz extends ANiz {

    public void ispisiNiz() throws LabisException{
        if (niz==null || niz.length==0){
            throw new LabisException();
        }
        for(int i = 0; i < niz.length; i++){
            System.out.print(niz[i] + " ");
        }
        System.out.println();
    }


    public double prosek() throws LabisException{
        if(niz ==null){
            throw new LabisException();
        }
        int zbir = 0;
        for(int i = 0; i < niz.length; i++){
            zbir+=niz[i];
        }
        return (double) zbir/niz.length;
    }

    public int najmanjiElem() throws LabisException{
        if (niz == null){
            throw new LabisException();
        }
        int min = Integer.MAX_VALUE;
        for(int i = 0; i < niz.length; i++){
            if (niz[i] < min){
                min = niz[i];
            }
        }
        return min;
    }

    public int indeksNajveceg() throws LabisException{
        if (niz==null){
            throw new LabisException();
        }

        int maxIndeks = 0;
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < niz.length; i++){
            if (niz[i]>max){
                max = niz[i];
                maxIndeks = i;
            }
        }
        return maxIndeks;
    }


    public void invertuj() throws LabisException{
        if (niz == null){
            throw new LabisException();
        }

        int pom;
        for (int i = 0; i < niz.length/2; i++){
            pom = niz[i];
            niz[i] = niz[niz.length-1-i];
            niz[niz.length-1-i] = pom;
        }
    }

    public double prosekParnih() throws LabisException{
        if (niz == null){
            throw new LabisException();
        }

        int zbir = 0;
        int brojac = 0;
        for (int i = 0; i < niz.length;i++){
            if(niz[i]%2==0){
                zbir+=niz[i];
                brojac++;
            }
        }
        return (double) zbir/brojac;

    }

    public void sortirajRastuce() throws LabisException{
        if (niz == null || niz.length ==0){
            throw new LabisException();
        }
        int pom;
        for (int i = 0; i < niz.length-1; i++){
            for (int j = i+1; j < niz.length; j++) {
                if (niz[i] > niz[j]) {
                    pom = niz[i];
                    niz[i] = niz[j];
                    niz[j] = pom;
                }
            }
        }
    }

    public boolean prostBroj(int broj) throws LabisException{
        if(niz == null){
            throw new LabisException();
        }
        int brojac = 0;
        if(broj == 1 || broj==2){
            return true;
        }
        for(int i =2; i <=broj; i++){
            if (broj%i==0){
                brojac++;
            }
        }

        return (brojac==0);
    }

    public Niz zameniProste(Niz niz) throws LabisException {
        for (int i = 0; i < niz.niz.length; i++){
            if (prostBroj(niz.niz[i])){
                niz.niz[i] = 1;
            }
        }
        return niz;
    }


    public int zbirMax3() throws LabisException {
        if (niz.length<3 || niz == null){
            throw new LabisException();
        }
        if (niz.length == 3){
            return niz[0]+niz[1]+niz[2];
        }

        int e1 = Integer.MIN_VALUE;
        int e2 = Integer.MIN_VALUE;
        int e3 = Integer.MIN_VALUE;

        for (int i = 0; i <niz.length; i++){
            if (niz[i] >= e1){
                e3 = e2;
                e2 = e1;
                e1 = niz[i];
            }
            else if (niz[i] >=e2){
                e3 = e2;
                e2 = niz[i];
            }
            else if (niz[i]>=e3){
                e3 = niz[i];
            }
        }
        return e1+e2+e3;

    }

    public int indeksTrecegNajveceg() throws LabisException{
        if (niz.length<3){
            throw new LabisException();
        }
        if (niz.length==3){
            if(niz[0] <= niz[1] && niz[0] <= niz[2]){
                return 0;
            }
            else if (niz[1] <= niz[0] && niz[1]<=niz[2]){
                return 1;
            }
            else {
                return 2;
            }
        }
        int e1 = Integer.MIN_VALUE;
        int e2 = Integer.MIN_VALUE;
        int e3 = Integer.MIN_VALUE;
        int i1 = -1;
        int i2 = -1;
        int i3 = -1;

        for (int i = 0; i < niz.length; i++){
            if (niz[i]>=e1){
                e3 = e2;
                e2 = e1;
                e1 = niz[i];
                i3 = i2;
                i2 = i1;
                i1 = i;
            }
            else if (niz[i]>=e2){
                e3 = e2;
                e2 = niz[i];
                i3 = i2;
                i2 = i;
            }
            else if (niz[i]>=e3){
                e3 = niz[i];
                i3 = i;
            }
        }
        return i3;
    }

    public void negativniPocetakPozitivniKraj(){
        int poslIndeks = 0;
        for (int i = 0; i < niz.length; i++){
            if (niz[i] < 0){
                int pom = niz[poslIndeks];
                niz[poslIndeks++] = niz[i];
                niz[i] = pom;
            }
        }
    }

    public int[] spojiDva(int[] a, int[] b) throws LabisException{
        int n1,n2;
        if (a == null){
            n1 = 0;
        }
        else{
            n1 = a.length;
        }
        if (b == null){
            n2 = 0;
        }
        else {
            n2 = b.length;
        }

        int niz[] = new int [n1+n2];
        int i = 0, j = 0, indeks = 0;

        while(i!=n1 && j!=n2){
            if(a[i]<b[j]){
                niz[indeks++] = a[i++];
            }
            else{
                niz[indeks++] = b[j++];
            }
        }
        while(i!=n1){
            niz[indeks++] = a[i++];
        }
        while(j!=n2){
            niz[indeks++] = b[j++];
        }
        return niz;
    }

    public int maxRazlDvaSusedna() throws LabisException{
        if(niz == null || niz.length<2){
            throw new LabisException();
        }
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < niz.length-1; i++){
            if (niz[i]>niz[i+1] && niz[i]-niz[i+1]>max){
                max = niz[i]-niz[i+1];
            }
        }
        return max;
    }

    public int maxRazlika() throws LabisException{
        if (niz == null || niz.length<2){
            throw new LabisException();
        }
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < niz.length-1; i++){
            for (int j = i+1; j< niz.length; j++){
                if (niz[i] > niz[j] && niz[i]-niz[j]>max){
                    max = niz[i]-niz[j];
                }
            }
        }
        if (max == Integer.MIN_VALUE){
            throw new LabisException();
        }
        return max;
    }

    public int fali() throws LabisException {
        if (niz[0]!=1){
            return 1;
        }
        for(int i = 0; i < niz.length; i++){
            if(niz[i+1]-niz[i]>1){
                return niz[i]+1;
            }
        }
        if (niz[niz.length-1]!=100){
            return 100;
        }
        throw new LabisException();
    }

    public int duzinaNjaduzegNeopadajucegPodniza(){
        int brojac = 1, max = Integer.MIN_VALUE;
        for (int i = 0; i < niz.length-1; i++){
            if (niz[i] <= niz[i+1]){
                brojac++;
            }
            else{
                if(brojac>max){
                    max = brojac;
                }
                brojac = 1;
            }
        }
        return max;
    }

//zameni svaki el proizvodom susedna dva, npr prvi se menja proizvodom prvog i drugog
    // za ostale npr ako imamo 1 2 3 dvojka se menja proizvodom 1 i 3

    public void zameniProizvodom() throws LabisException{

        if(niz == null || niz.length < 2){
            throw new LabisException();
        }
        int tekuci;
        int prethodni = niz[0];

        for (int i = 0; i < niz.length; i++){
            tekuci = niz[i];
            niz[i] = prethodni*niz[i+1];
            prethodni = tekuci;
        }
        niz[niz.length-1]*=prethodni;
    }

    //premesti k elem sa poc na kraj niza
    public void rotirajJednoMestoDesno(){
        int pom = niz[niz.length-1];
        for (int i = niz.length-1; i>0; i--){
            niz[i] = niz[i-1];
        }
        niz[0] = pom;
    }

    public void pomeriMesta(int k) throws LabisException{
        if (niz == null || niz.length<k){
            throw new LabisException();
        }
        for (int i = 0; i < k; i++){
            rotirajJednoMestoDesno();
        }
    }
    public int brojPojavljivanja(int elem){
        if (niz == null || niz.length == 0){
            return 0;
        }
        int brojac = 0;
        for (int i = 0; i < niz.length; i++){
            if(niz[i] == elem){
                brojac++;
            }
        }
        return brojac;
    }

    public boolean postoji(int niz[], int el){
        for (int i = 0; i <niz.length; i++){
            if(niz[i] == el){
                return true;
            }
        }
        return false;
    }

    public int brojBrojeva(){
        if (niz == null || niz.length == 0){
            return 0;
        }
        int[] nizBezPonavljanja = new int[niz.length];
        int indeks = 0;
        for (int i = 0; i < niz.length; i++){
            if (niz[i]==brojPojavljivanja(niz[i]) && !postoji(nizBezPonavljanja, niz[i])){
                nizBezPonavljanja[indeks++] = niz[i];
            }
        }
        return indeks;

    }

    //svi br veci ili = od sledbenika prebacuje u listu

    public boolean jeVeciJednakOdSledbenika(int indeks){
        if (indeks == niz.length-1){
            return false;
        }
        int elementNiza = niz[indeks];
        for (int i = indeks+1; i < niz.length; i++){
            if (elementNiza<niz[i]){
                return false;
            }
        }
        return true;
    }

    public CvorJSListe vratiListuOdNiza() throws LabisException{
        if (niz==null || niz.length<2){
            throw new LabisException();
        }
        JSLista lista = new JSLista();
        for (int i = 0; i < niz.length; i++){
            if (jeVeciJednakOdSledbenika(i)){
                lista.dodajNaKraj(niz[i]);
            }
        }
        return lista.prvi;
    }

    public int vratiElKojiSePonavlja() throws LabisException{
        if (niz == null || niz.length == 0){
            throw new LabisException();
        }
        if (niz.length == 1){
            return niz[0];
        }
        for (int i = 0; i < niz.length-1; i+=2){
            if (niz[i]!=niz[i+1]){
                return niz[i];
            }
        }
        if (niz[niz.length-1]!=niz[niz.length-2]){
            return niz[niz.length-1];
        }
        throw new LabisException();
    }
}
