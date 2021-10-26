# Project 2 CSCI 5611

- Infant Derrick Gnana Susairaj (gnana014)

### About

For part 2:

I wanted to keep it pretty simple with this project. I wanted to be able to recreate a the animation that was played in class of a cloth colliding with a sphere. I also wanted to make sure you can see the collision from any angle desired. I also gave the sphere free motion so that it can move around and collide into the cloth at different more interesting angles.

### Code

You can access the code [here](https://github.com/InfantDerrick/csci5611/tree/master/projects/proj2). 

#### Cloth Mechanics
```processing
  for(int i = 0; i < nx - 1; i++){
      for(int j = 0; j < ny; j++){
        Vec3 e = p[i+1][j].minus(p[i][j]);
        float l = e.length();
        e.normalize();
        float v1 = dot(e, v[i][j]);
        float v2 = dot(e, v[i+1][j]);
        float f = -ks * (10 - l) - kd * (v1 - v2);
        vn[i][j].add(e.times(f*dt));
        vn[i+1][j].subtract(e.times(f*dt)); 
      }
    }
    for(int i = 0; i < nx; i++){
      for(int j = 0; j < ny - 1; j++){
        Vec3 e = p[i][j+1].minus(p[i][j]);
        float l = e.length();
        e.normalize();
        float v1 = dot(e, v[i][j]);
        float v2 = dot(e, v[i][j+1]);
        float f = -ks * (10 - l) - kd * (v1 - v2);
        vn[i][j].add(e.times(f * dt));
        vn[i][j+1].subtract(e.times(f*dt)); 
      }
    }
 }
```
#### Cloth Mechanics
```processing
    for(int i = 0; i < nx; i++){
      for(int j = 0; j < ny; j++){
        
        float d = spherePos.distanceTo(p[i][j]);
        if(d < sphereR + 0.09){
          Vec3 n = (spherePos.minus(p[i][j])).times(-1);
          n.normalize();
          Vec3 bounce = n.times(dot(v[i][j],n));
          v[i][j].subtract(bounce.times(1.3));
          p[i][j].add(n.times(.1 + sphereR - d));
        }else{
          p[i][j].add(v[i][j].times(dt));
        }
      }
    }
```

### Media

[Main Demo](https://youtu.be/C6pF1_yd_cU).

[Enviornment Demo](https://youtu.be/ftYPIYkWxxQ).

[Movement Demo](https://youtu.be/rlY_FiM6U8k).

