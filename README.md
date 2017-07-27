# XMLDomParser
Test XML Parsing with Java
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import java.util.Enumeration;
import java.util.Scanner;
import java.util.zip.*;

import javax.xml.parsers.DocumentBuilder;
import javax.xml.parsers.DocumentBuilderFactory;
import org.w3c.dom.Document;
import org.w3c.dom.NodeList;
import org.w3c.dom.Node;
import org.w3c.dom.Element;


@SuppressWarnings("unused")
public class HelloWorld {

	public static void main(String[] args) {
		
		System.out.println("Hello " + args[0] + " And " + args[1]);
		try
		{	
			@SuppressWarnings("resource")
			ZipFile zipFile = new ZipFile(args[2]);
			Enumeration<? extends ZipEntry> entries = zipFile.entries();
			
			while(entries.hasMoreElements()){
		        ZipEntry entry = entries.nextElement();
		        System.out.println(entry);
		        InputStream stream = zipFile.getInputStream(entry);
		        DocumentBuilderFactory dbFactory = DocumentBuilderFactory.newInstance();
				DocumentBuilder dBuilder = dbFactory.newDocumentBuilder();
				Document doc = dBuilder.parse(stream);
				doc.getDocumentElement().normalize();
				System.out.println("Root element :" + doc.getDocumentElement().getNodeName());
				
		        stream.close();
		    }
			
		}
		catch(Exception e) {
			e.printStackTrace();
		}
		finally {
			
		}
		
	}

}
