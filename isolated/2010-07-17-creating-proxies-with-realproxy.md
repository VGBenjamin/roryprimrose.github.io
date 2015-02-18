---
title: Creating proxies with RealProxy
categories : .Net, .Net
tags : WCF, WCF
date: 2010-07-17 19:53:24 +10:00
---


public class TestProxy<T> : RealProxy
{
    public TestProxy()
        :base(typeof(T))
    {
    }

    [SecurityPermission(SecurityAction.LinkDemand, Flags = SecurityPermissionFlag.Infrastructure)]
    [DebuggerStepThrough]
    public override IMessage Invoke(IMessage msg)
    {
        Debug.Assert(msg != null, "No message has been provided");

        ReturnMessage responseMessage;
        Object response = null;
        Exception caughtException = null;

        try
        {
            String methodName = (String)msg.Properties["__MethodName"];
            Type[] parameterTypes = (Type[])msg.Properties["__MethodSignature"];
            MethodBase method = typeof(T).GetMethod(methodName, parameterTypes);

            Object[] parameters = (Object[])msg.Properties["__Args"];

            // ______________________________________________________________________________
            //
            // Start the logic for handling the method invocation on this proxy
            // ______________________________________________________________________________

            Console.WriteLine("Invoking " + method.Name + " with the following parameters:");

            for (int index = 0; index < parameters.Length; index++)
            {
                Console.WriteLine(parameterTypes[index].Name + " - " + parameters[index]);
            }

            // ______________________________________________________________________________
            //
            // End the logic for handling the method invocation on this proxy
            // ______________________________________________________________________________
        }
        catch (Exception ex)
        {
            // Store the caught exception
            caughtException = ex;
        }

        IMethodCallMessage message = msg as IMethodCallMessage;

        // Check if there is an exception
        if (caughtException == null)
        {
            // Return the response from the service
            responseMessage = new ReturnMessage(response, null, 0, null, message);
        }
        else
        {
            // Return the exception thrown by the service
            responseMessage = new ReturnMessage(caughtException, message);
        }

        // Return the response message
        return responseMessage;
    }
}
{% endhighlight %}



class Program
{
    static void Main(string[] args)
    {
        TestProxy<ITester> proxy = new TestProxy<ITester>();
        ITester tester = proxy.GetTransparentProxy() as ITester;

        tester.RunTest("This is the message", true, Guid.NewGuid());

        Console.ReadKey();
    }
}

public interface ITester
{
    void RunTest(String message, Boolean flag, Guid marker);
}
{% endhighlight %}
    
Invoking RunTest with the following parameters:
String - This is the message
Boolean - True
Guid - aade8728-9ca3-4919-9080-14090b5b016b
{% endhighlight %}