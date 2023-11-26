## Building Url Dynamically
##Variable Rules And URL Building

from flask import Flask,redirect,url_for
### WSGI Application, used to communicate between the web server and web application that i am trying to create.
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello World, from Flask!"

# directs to URL
@app.route('/guests')
def welcome():
    return "Welcome to my page"
#
@app.route("/success/<int:score>")
def success(score):
    return "<html><body><h1>The Result is PASSED</h1></body></html>"

@app.route("/fail/<int:score>")
def fail(score):
    return "<html><body><h1>The Result is FAILED</h1></body></html>"

#Result Checker
@app.route('/results/<int:marks>')
def results(marks):
    result=""
    if marks>50:
        result='fail'
    else:
        result='success'
        return redirect(url_for(results,score=marks))
    


if __name__=='__main__':
    app.run(debug=True)
