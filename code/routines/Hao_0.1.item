package routines;

import java.util.Date;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

/*
 * user specification: the function's comment should contain keys as follows: 1. write about the function's comment.but
 * it must be before the "{talendTypes}" key.
 * 
 * 2. {talendTypes} 's value must be talend Type, it is required . its value should be one of: String, char | Character,
 * long | Long, int | Integer, boolean | Boolean, byte | Byte, Date, double | Double, float | Float, Object, short |
 * Short
 * 
 * 3. {Category} define a category for the Function. it is required. its value is user-defined .
 * 
 * 4. {param} 's format is: {param} <type>[(<default value or closed list values>)] <name>[ : <comment>]
 * 
 * <type> 's value should be one of: string, int, list, double, object, boolean, long, char, date. <name>'s value is the
 * Function's parameter name. the {param} is optional. so if you the Function without the parameters. the {param} don't
 * added. you can have many parameters for the Function.
 * 
 * 5. {example} gives a example for the Function. it is optional.
 */
public class Hao {

    /**
     * helloExample: not return value, only print "hello" + message.
     * 
     * 
     * {talendTypes} String
     * 
     * {Category} User Defined
     * 
     * {param} string("world") input: The string need to be printed.
     * 
     * {example} helloExemple("world") # hello world !.
     */
    public static void helloExample(String message) {
        if (message == null) {
            message = "World"; //$NON-NLS-1$
        }
        System.out.println("Hello " + message + " !"); //$NON-NLS-1$ //$NON-NLS-2$
    }
    
    /**
     * 从字符串中取出url
     * @param ligne
     * @return
     */
    public static String get_url(String ligne)
    {
    	if(ligne==null)
    	{
    		return null;
    	}
    	else
    	{
    		Pattern p = Pattern.compile("<!-- saved from url=\\([0-9]+\\)(https:[^\t^ ^\r^\n]+) -->");
    		Matcher m = p.matcher(ligne);
    		if(m.find())
    		{
    			return m.group(1);
    		}
    		else
    		{
    			return null;
    		}
    	}
    }
    
    /**
     * 从链接中取出ID
     * @param ligne_url
     * @return
     */
    public static String get_id_from_url(String ligne_url)
    {
    	if(ligne_url==null)
    	{
    		return null;
    	}
    	else
    	{
    		Pattern p = Pattern.compile("<!-- saved from url=\\([0-9]+\\)https://www.meetic.fr/d/profile-display/([0-9]+)\\?[^ ]+ -->");
    		Matcher m = p.matcher(ligne_url);
    		if(m.find())
    		{
    			return m.group(1);
    		}
    		else
    		{
    			return null;
    		}
    	}
    }
    
    /**
     * Get the informations of the user from the content
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_infos_from_contenu(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null)
    	{
    		return null;
    	}
    	else
    	{
    		Pattern p = Pattern.compile(" ");
    		Matcher m = p.matcher(ligne_contenu);
    		String resultat = null;
    		switch (type){
    			case "name":
    				p = Pattern.compile("<title>([^<]+) - Meetic</title>");
    				m = p.matcher(ligne_contenu);
    				if(m.find())
    					resultat = m.group(1);
    				break;
    			case "age":
    				p = Pattern.compile("ctrl\\.age}\">([0-9]+) ans</span>");
    				m = p.matcher(ligne_contenu);
    				if(m.find())
    					resultat = m.group(1);
    				break;
    			case "photo":
    				p = Pattern.compile("class=\"pictures-main-area__picture\" style=\"background-image: url\\(&quot;([^&]+)&quot;\\);\"></a>");
    				m = p.matcher(ligne_contenu);
    				if(m.find())
    					resultat = m.group(1);
    				else
    				{
    					p = Pattern.compile("class=\"pictures-main-area__picture.+\" style=\"background-image: url\\(&quot;([^&]+)&quot;\\);\"></a>");
        				m = p.matcher(ligne_contenu);
        				if(m.find())
        					resultat = m.group(1);
    				}
    				break;
    			default:
    				break;
    		}
    		return resultat;
    	}
    }
    
    
    
    /**
     * reflist + div
     * Récupérer les informations de la partie "Ma personnalité"
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_personnalite_from_contenu(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "reflist\\."+type+"\">[^<]+</div>(<!---->)+<[^>]+>([^<]+)</div>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    			resultat = m.group(2);
    		return resultat;
    	}
    }
    
    
    /**
     * reflist + span
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_mode_from_contenu(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "reflist\\."+type+"\">[^<]+</div>(<!---->)+<[^>]+>([^<]+)</span>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    			resultat = m.group(2);
    		return resultat;
    	}
    }
    
    
    /**
     * ctrl + span
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_title_from_contenu(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "ctrl\\."+type+"\">([^<]+)</span>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    			resultat = m.group(1);
    		return resultat;
    	}
    }
    
    /**
     * ctrl + div
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_physique_from_contenu(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "ctrl\\."+type+"\">([^<]+)</div>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    			resultat = m.group(1);
    		return resultat;
    	}
    }
    
    
    
    /**
     * 
     * @param ligne_contenu
     * @return
     */
    public static Integer get_number_from_string(String ligne_contenu)
    {
    	if(ligne_contenu==null)
    		return null;
    	else
    	{
    		Pattern p = Pattern.compile("[0-9]+");
    		Matcher m = p.matcher(ligne_contenu);
			if(m.find())
				return Integer.valueOf(m.group());
			else
				return null;
    	}
    }
    
    
    /**
     * 
     * @param ligne_contenu
     * @return
     */
    public static Boolean get_boolean_from_string(String ligne_contenu)
    {
    	if(ligne_contenu==null)
    		return null;
    	else
    	{
    		String tmp_string = ligne_contenu.trim().toLowerCase();
    		if(tmp_string.equals("yes") 
    				|| tmp_string.equals("oui")
    				|| tmp_string.equals("y")
    				|| tmp_string.equals("o"))
    			return true;
    		else
    			return false;
    	}
    }
    
    
    
    
    
    
    
    /**
     * 
     * @param ligne_contenu
     * @param type
     * @return
     */
    public static String get_search_card_span(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "search_card\\."+type+"\">[^<]+</span>( <!---->)+<[^>]+>([^<]+)</span>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    			resultat = m.group(2);
    		return resultat;
    	}
    }
    
    
    /**
     * get search age
     * @param ligne_contenu
     * @param choix 1-FROM 2-TO
     * @return
     */
    public static Integer get_search_age(String ligne_contenu, int choix)
    {
    	if(ligne_contenu==null)
    		return null;
    	else
    	{
    		Pattern p = Pattern.compile("de ([0-9]+) ([a-zA-Z]+ )?à ([0-9]+) ");
    		Matcher m = p.matcher(ligne_contenu);
			if(m.find())
			{
				if(choix == 1)
					return Integer.valueOf(m.group(choix));
				else
					return Integer.valueOf(m.group(3));
			}
			else
				return null;
    	}
    }
    
    
    
    public static Integer get_birthday(Integer age)
    {
    	if(age==null)
    		return null;
    	else
    	{
    		Date tmp_date = TalendDate.getCurrentDate();
    		String tmp_string = TalendDate.formatDate("yyyy", tmp_date);
    		int tmp_int = Integer.valueOf(tmp_string);
    		return (tmp_int-age);
    	}
    }
    
    
    
    public static String get_interest(String ligne_contenu, String type)
    {
    	if(ligne_contenu==null || type==null)
    	{
    		return null;
    	}
    	else
    	{
    		String resultat = null;
    		String string_compile = "interests\\."+type+"\">[^<]+</h2>(.+)<!----><!----><!----></div></div>";
    		Pattern p = Pattern.compile(string_compile);
    		Matcher m = p.matcher(ligne_contenu);
    		if(m.find())
    		{
    			resultat = "";
    			String resultat_tmp = m.group(1);
    			p = Pattern.compile("value\">([^<]+)</div>");
    			m = p.matcher(resultat_tmp);
    			while(m.find())
    			{
    				resultat += m.group(1)+",";
    			}
    		}
    		return resultat;
    	}
    }
    
}
