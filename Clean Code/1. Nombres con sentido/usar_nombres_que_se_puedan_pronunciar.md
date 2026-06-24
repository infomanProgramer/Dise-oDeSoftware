# Usar nombres que se puedan pronunciar

Crear nombre pronunciables, sino lo puede pronunciar, no podrá explicarlo sin parecer tonto. Es un hecho importante ya que la programación es una actividad social.

Por ejemplo compare:

~~~c#
class DtaRcrd102 
{
    private Date genymdhms; 
    private Date modymdhms; 
    private final String pszqint = “102”;
}
~~~

con

~~~c#
class Customer
{
    private Date generationTimestamp;
    private Date modificationTimestamp;
    private final String recordId = “102”;
}
~~~
