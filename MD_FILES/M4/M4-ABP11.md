
# M4-ABP11

---

    /**
     * @author Jarod Smith
     */
    package m4ABP11;

    public class Trabajador {
        //ATRIBUTOS
        private String nombres;
        private String apellidos;
        private String run;
        private int edad;
    
        //MÉTODOS ACCESORES Y MODIFICADORES
        public String getNombres() {
            return nombres;
        }
    
        /**
         * 
         * @param nombres
         */
        public void setNombres(String nombres) {
            this.nombres = nombres;
        }
    
        public String apellidos() {
            return apellidos;
        }
    
        /**
         * 
         * @param apellidos
         */
        public void setApellidos(String apellidos) {
            this.apellidos = apellidos;
        }
    
        public String getRun() {
            return run;
        }
    
        /**
         * 
         * @param run
         */
        public void setRun(String run) {
            this.run = run;
        }
    
        public int getEdad() {
            return edad;
        }
    
        /**
         * 
         * @param edad
         */
    
        public void setEdad(int edad) {
            this.edad = edad;
        }
    
        //MÉTODO CONSTRUCTOR SIN ARGUMENTOS
        public Trabajador(){}
    
        //MÉTODO CONSTRUCTOR CON ARGUMENTOS
        /**
         * 
         * @param nombres
         * @param apellidos
         * @param rut
         * @param edad
         */
        public Trabajador(String nombres, String apellidos, String run, int edad) {
            this.nombres = nombres;
            this.apellidos = apellidos;
            this.run = run;
            this.edad = edad;
        }
    
        /**
         * 
         * @return nombre y apellido del trabajador
         */
        public String nombreCompleto() {
            return nombres + " " + apellidos;
        }
    
        /**
         * 
         * @return int unicamente digitos del run
         */
        public int descomponerRun() {
            return Integer.parseInt(run.split("-")[0]);
        }
    
        @Override
        public String toString() {
            return "Trabajador \nNombres: " + nombres + ", \nApellidos: " + apellidos +
                    ", \nRUT: " + run + ", Edad: " + edad;
        }
    
    
        public static void main(String[] args) {
            // TODO Auto-generated method stub
            Trabajador trabajador1 = new Trabajador();
    
            trabajador1.setNombres("Armando");
            trabajador1.setApellidos("Casas");
            trabajador1.setRun("123456-7");
            trabajador1.setEdad(35);
    
            Trabajador trabajador2 = new Trabajador("Alam", "Brito", "456789-0", 36);
            Trabajador trabajador3 = new Trabajador("Elba", "Surero", "4562114-5", 25);
    
    
            System.out.println(trabajador1.toString());
            System.out.println("------");
            System.out.println(trabajador2.toString());
            System.out.println("------");
            System.out.println(trabajador3.toString());
    
        }
    }
