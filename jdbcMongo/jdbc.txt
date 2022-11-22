package jdbcMongo;

import com.mongodb.*;

public class jdbc {

	public static void main(String[] args) {
		//  create collection
		MongoClient mongo = new MongoClient("localhost",27017);
		
		DB db = mongo.getDB("mydb");
		
		
		//create a collection
		DBCollection col = db.getCollection("students");
		
		//insert a document
		BasicDBObject d1 = new BasicDBObject("roll",1).append("name", "sumit").append("age", 20);
		BasicDBObject d2 = new BasicDBObject("roll",9).append("name", "atharv").append("age", 19);
		
		//insert in collection
		col.insert(d1);
		col.insert(d2);
		
		//display doc
		DBCursor cursor = col.find();
		
		while(cursor.hasNext())
			System.out.println(cursor.next());

	}

}
