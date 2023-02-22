# M4-ABP_6

---

    package m4ABP6;

    import javax.swing.*;

    public class M4ABP6 {

        public static void main(String[] args) {
            // TODO Auto-generated method stub
            String password = "12345";
            String capture = "";
            int tries = 3;
            int count = 0;

            do {
                capture = JOptionPane.showInputDialog("Ingrese su contraseña");
                if(!capture.equals(password)) {
                    System.out.println("[ERROR] Contraseña incorrecta.");
                    count++;
                    if(count == tries) {
                        System.out.println("INTENTOS MÁXIMOS PERMITIDOS");
                    }
                }else {
                    System.out.println("ACCESO GARANTIZADO");
                }
            }while(!password.equals(capture) && count < tries);
        }
    }
