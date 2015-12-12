# sanju\

package com.rail;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.URL;
import java.net.URLConnection;

public class ErailHttpURLConnection {

	public static void getErailInfo(){
		String urlAddress = "http://111.118.213.140/js/cmp/stations.js?v=092221";
		urlAddress ="http://111.118.213.140/js4/cmp/erail_all_34.js?v=09322222925";
		urlAddress = "http://runningstatus.in/status/12392-yesterday";
		//urlAddress ="http://www.ietf.org/rfc/rfc2616.txt" ;  //for java documentaion for networking.
		try{
			URL url = new URL(urlAddress);
			URLConnection urlConnection = url.openConnection();
			BufferedReader in = new BufferedReader(new InputStreamReader(urlConnection.getInputStream()));
			String str = "";
			//System.out.println("<div class=\"runningstatus-widget-content\"><p>");
			while((str = in.readLine())!=null){
				
				if(str.contains("<div class=\"runningstatus-widget-content\"><p>")){
					int startIndex = str.indexOf("<div class=\"runningstatus-widget-content\"><p>");
					int lastIndexOf = str.indexOf("</p></div>");
					//System.out.println(startIndex+"  "+lastIndexOf);
					System.out.println(str.substring(startIndex,lastIndexOf).replace("<div class=\"runningstatus-widget-content\"><p>", ""));
				}
				
			}
			
		}catch(Exception e){
			e.printStackTrace();
		} 
	}
	
	public static void main(String[] args) {
		getErailInfo();
	}
}


