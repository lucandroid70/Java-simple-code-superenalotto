# Java-simple-code-superenalotto
Java simple code superenalotto


/**
 * 
 */
/**
 * @author lucandroid70
 *
 */
    import java.util.Random;
     
    public class Estrattore {
     
    	    	
        private int[] base;
        private boolean[] scelti;
     
        public Estrattore(int[] pBase) {
            this.base = new int[pBase.length];
            this.scelti = new boolean[pBase.length];
            System.arraycopy(pBase, 0, this.base, 0, pBase.length);
        }
     
        public int[] estrai(int pNum) {
            if (pNum > this.base.length) {
                throw new IllegalArgumentException("Impossibile estrarre un array casuale più grande dell'array di base");
            }
            int[] retval = new int[pNum];
            Random rand = new Random();
            int random = 0;
            for (int i = 0; i < pNum; i++) {
                do {
                    random = rand.nextInt(this.base.length);
                } while (this.scelti[random]);
                retval[i] = this.base[random];
                this.scelti[random] = true;
            }
            return retval;
        }
     
        public void resetScelti(){
            this.scelti=new boolean[this.base.length];
        }
     
        public static void main(String... args) {
            int[] base = new int[90];
            for (int i = 0; i < 90; i++) {
                base[i] = i + 1;
            }
            System.out.println("Tool Java creato da lucandroid70@gmail.com");
            Estrattore estrai = new Estrattore(base);
            int[] ret= new int[6];
            for (int i = 0; i < 6; i++) {
                ret=estrai.estrai(ret.length);
                System.out.print("Sestina numero "+(i+1)+": ");
                for (int j = 0; j < ret.length; j++) {
    
                	System.out.print(ret[j] + " ");
                   
                }
                System.out.println();
                estrai.resetScelti();
                
            }
            { 
            	System.out.println("Tool Java creato da lucandroid70@gmail.com");
            	System.out.println("Buona fortuna e ricirdati di me se vinci");
            	System.out.println("questo è il mio IBAN:021225442121254200");
            }
        
        }
    
    }
