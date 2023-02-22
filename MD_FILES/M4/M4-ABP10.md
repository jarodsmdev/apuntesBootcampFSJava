# M4 ABP10

---

    /**
     * @author Jarod Smith
     */
    package m4ABP10;

    public class Trabajadores {
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
        public Trabajadores(){}
    
        //MÉTODO CONSTRUCTOR CON ARGUMENTOS
        /**
         * 
         * @param nombres
         * @param apellidos
         * @param rut
         * @param edad
         */
        public Trabajadores(String nombres, String apellidos, String run, int edad) {
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
            return "Trabajadores \nNombres: " + nombres + ", \nApellidos: " + apellidos +
                    ", \nRUT: " + run + ", Edad: " + edad;
        }
    }
