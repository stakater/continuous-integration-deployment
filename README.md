# continuous-delivery-deployment
what is continuous delivery? what is continuous deployment? what is release strategy?

## Deploying and Promoting Your Application

The key to deploying any application in a reliable, consistent manner is constant practice: Use the same process to deploy to every environment, including production.

### Modeling Your Release Process and Promoting Builds

In particular, it is important to capture:

- What stages a build has to go through in order to be released (for example, integration testing, QA acceptance testing, user acceptance testing, staging, production)
- What the required gates or approval are
- For each gate, who has the authority to approve a build passing throughthat gate

At the end of this exercise, you might end up with a diagram similar to this:

Once you’ve created this diagram, you can create placeholders for each part of your release process in the tool you use for managing deployments. Once this is done, it should be possible for the people responsible for approvals to approve, using your tool, a particular build moving through a gate in the release process.

The other essential facility that must be provided by the tool you use to manage your deployment pipeline is the ability, for each stage, to see which builds have passed all the previous stages in the pipeline and are hence ready for the next stage. It should then be possible to choose one of these builds and press a button to have it deployed. This process is known as promotion. Promoting builds at the press of a button is what turns the deployment pipeline into a pull system, giving everybody involved in the delivery process the ability to manage their own work. Analysts and testers can self-service deployments for exploratory testing, showcasing, or usability testing. Operations personnel can deploy any version of their choice to staging or production at the press of a button.

## Emergency Fixes

In every system, there comes a moment when a critical defect is discovered and has to be fixed as soon as possible. In this situation, the most important thing to bear in mind is: Do not, under any circumstances, subvert your process. Emergency fixes have to go through the same build, deploy, test, and release process as any other change. Why do we say this? Because we have seen so many occasions where fixes were made by logging directly into production environments and making uncontrolled changes.

## Continuous Deployment

The idea is simply this: I take my pipeline and make the final step—deployment to production—automatic. That way, if a check-in passes all the automated tests, it gets deployed directly to production. In order for this not to cause breakages, your automated tests have to be fantastic—there should be automated unit tests, component tests, and acceptance tests (functional and nonfunctional) covering your entire application. You have to write all your tests—including acceptance tests—first, so that only when a story is complete will check-ins pass the acceptance tests.

Perhaps most importantly, continuous deployment forces you to do the right thing (as Fitz points out in his blog post). You can’t do it without automating your entire build, deploy, test, and release process. You can’t do it without a comprehensive, reliable set of automated tests. You can’t do it without writing system tests that run against a production-like environment. That’s why, even if you can’t actually release every set of changes that passes all your tests, you should aim to create a process that would let you do so if you choose to.

> So what magic happens in our test suite that allows us to skip having a manual Quality Assurance step in our deploy process? The magic is in the scope, scale and thoroughness. It’s a thousand test files and counting. 4.4 machine hours of automated tests to be exact. Over an hour of these tests are instances of Internet Explorer automatically clicking through use cases and asserting on behaviour, thanks to Selenium. The rest of the time is spent running unit tests that poke at classes and functions and running functional tests that make web requests and assert on results.

## References

- [Continuous Delivery Book](...)
- [Continuous Deployment by Timothy](http://timothyfitz.com/2009/02/08/continuous-deployment/)
- [Continuous Deployment at IMVU: Doing the impossible fifty times a day.](http://timothyfitz.com/2009/02/10/continuous-deployment-at-imvu-doing-the-impossible-fifty-times-a-day/)
