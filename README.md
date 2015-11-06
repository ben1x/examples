package datasource;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

import javax.swing.JOptionPane;

public class Serviciodb {
	private static Connection conectar=null;
	private static final String url = "jdbc:mysql://localhost/mundo";
	private static final String usuario = "root";
	private static final String contrasena = "";
	private static final String driver = "com.mysql.jdbc.Driver";

	private Serviciodb(){
		
	}
	
	 public static void conectarse(){
	        try {
	            Class.forName(driver);
	            conectar = DriverManager.getConnection(url, usuario,contrasena);
	            //System.out.println("Conectado");
	        } catch (ClassNotFoundException ex1) {
	        	ex1.printStackTrace();
	        	  JOptionPane.showMessageDialog(null, "Fue imposible conectarse al servidor."
	                      , "Error de conexion", JOptionPane.ERROR_MESSAGE);
	        } catch (SQLException ex2) {
	        	JOptionPane.showMessageDialog(null, "Fue imposible conectarse al servidor."
	                    + "Porfavor siga los pasos para para ejecutar este programa."
	                    + "\nPrimero: Inicie su servicio de base de datos si no esta iniciado.\n"	                    
	                    + "Segundo: Vuelva a ejecutar este programa", "Error del servidor", JOptionPane.ERROR_MESSAGE);
	                ex2.printStackTrace();
	                //System.exit(0);
	        }
	    }
	 
	 
	 public static Connection getConnection(){
		 if(conectar==null){
			 conectarse();
		 }
		 return conectar;
	 }
	 
	 public static void main(String[] args) {
		Serviciodb.getConnection();
	}
	

}
