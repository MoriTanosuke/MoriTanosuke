--- 
wordpress_id: 148
layout: post
title: Mocking dependencies in unit tests using JMockIt
wordpress_url: http://blog.kopis.de/?p=148
---

    <p><em>Ein weiterer Blogpost aus dem Firmenblog, wieder in Englisch.</em></p>
<h2>Garage &amp; GarageTest</h2>
<p>This test case demonstrate the use of <a href="http://code.google.com/p/jmockit/">JMockIt</a> and it's <em>Expectations</em> to resolve dependencies in unit tests. <em>Expectations </em>are a way to easily mock the behavior of an object in unit tests, without creating interfaces, classes and other overhead. Take a look at the full unit test first, and I'll explain what's done there later. You can find the interface <code>Garage</code> and the classes <code>CheapGarage</code> and <code>EngineFactory</code> at the end of this blogpost.</p>
<p>Now, back to the method <code>testRepairWithExpectationEngineFactory()</code>. The <code>EngineFactory</code> is a dependency buried down in the <code>CheapGarage</code> class that is responsible for replacing the <code>Engine</code> in a <code>Car</code>. There is a mocked instance of <code>EngineFactory</code> in this unit test that will return a new <code>DieselEngine</code> every time the method <code>instantiate()</code> is called with any kind of argument. This way I can control exactly how the hidden call to a factory behaves.  JMockIt has a bunch of other useful features and I recommend it for all unit tests. If you care about your tests and try to avoid testing dependencies instead of your logic, then you should start using JMockIt today. :-)</p>
<p><p><a href="http://gist.github.com/615103">http://gist.github.com/615103</a></p></p>
  
