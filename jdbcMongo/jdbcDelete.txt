package jdbcMongo;

import com.mongodb.*;

public class jdbcDelete {

	public static void main(String[] args) {
		// create connection
		
		MongoClient mongo = new MongoClient("localhost",27017);
		
		DB db = mongo.getDB("mydb");
		
		DBCollection col = db.getCollection("students");
		
		//before delete 
		DBCursor cursor = col.find();
		while(cursor.hasNext())
			System.out.println(cursor.next());
		
		
		BasicDBObject d3 = new BasicDBObject("name","atharva");
		col.remove(d3);
		
		DBCursor cursor1 = col.find();
		while(cursor1.hasNext())
			System.out.println(cursor1.next());
		
		 

	}

}
