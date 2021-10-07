``INCS_741-FVA2-2021FA-VR-Assignment2``
# Extended Euclidean Algorithm Implementation



# Install docker
**Windows**: to install docker for windows you can get the docker engine installer from the 
link below.

https://docs.docker.com/desktop/windows/install/

![image](https://user-images.githubusercontent.com/27841802/136328403-c88a13eb-b315-4ce4-b361-eb6a04cb6399.png)

## Docker Python Application

**1. Create a directory**

Directory is required to organize files. Create a Directory **Assignment**.

**2. Create a Python File**

Create a Python file. Save this file as **extEuclid.py** file.

``` bash
def extEuclid(a, b):
    if b < 0 or b > a:
        return
    ##Initialize variables
    r = [a, b]
    x = [1, 0]
    y = [0, 1]
    
    while r[1] != 0:
        q = r[0] // r[1]
        
        r[0], r[1] = r[1], r[0] % r[1] 
                
        x[0], x[1] = x[1], x[0] - q * x[1]
        y[0], y[1] = y[1], y[0] - q * y[1]
                        
    return r[0], x[0], y[0]

def main():
    aprime = input(">>Please input the value of a>>: ")
    try:
        aprime = int(aprime)
    except:
        print("Please input a positive integer <a>.")
        return

    bprime = input(">>Please input the value of b>>: ")
    try:
        bprime = int(bprime)
    except:
        print("Please input an integer less than <a>!")
        return

    d, x, y = extEuclid(aprime, bprime)
    print()
    print(46*"=")
    print("The result of a = %d, b = %d: " % (aprime, bprime))
    print("%6s GCD(%d, %d) = %d, x = %d, y = %d" % (">>>", aprime, bprime, d, x, y))
    print("%6s The expression is: %d = %d * %d + %d * %d" % (">>>", d, x, aprime, y, bprime))

    return

if __name__ == "__main__":
    main()

```


**3. Create a Dockerfile**

After creating a Python file, we need to create a Dockerfile which contains instructions for the Docker. Dockerfile does not contain any file extension. Save it with Dockerfile name.

```

FROM python:3
ADD extEuclid.py /
CMD [ "python","./extEuclid.py" ]

```


**Now we have Dockerfile parallel to extEuclid.py inside the Assignment directory.**

## Build Docker Image

Run the following command:

```

docker build -t exteulid .

```

![image](https://user-images.githubusercontent.com/27841802/136331410-91b2f532-ef61-4adc-9888-aea195bc7b44.png)


## Run Docker Image

After creating image successfully. Now we can run docker by using run command. The following command is used to run exteulid.


![image](https://user-images.githubusercontent.com/27841802/136331050-ab4ccb1e-e125-4606-a100-83c82104a35d.png)




## Group 9

- Bin Yang
- Xi Rui
- Xuemei Shang


## References

- https://docs.docker.com/desktop/windows/install/
- https://www.wintellect.com/containerize-python-app-5-minutes/
- https://docs.docker.com/reference/
- https://docker-curriculum.com/
- https://www.javatpoint.com/docker-java-example



