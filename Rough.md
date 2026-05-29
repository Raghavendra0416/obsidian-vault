```Javascript
user.routes.js
//Imports

const express =require('express');

const router = express.Router();

const User =require('../models/user.model.js')

  

//GET Users By ID

router.get('/:id',async (req,res)=>{

    console.log('GET Request');

    try{

        const userId = req.params.id;

        //Fetching User By ID

        const user = await User.findById(req.params.id);

        if (!user) {

            return res.status(404).json({ message: "User not found" });

        }

  

        //Response Back

        res.status(200).json({ message: `${user} fetched successfully` });

    }catch(err){

        //If Error

        res.status(500).json({ error: error.message });

    }

});

  

// 3. GET All Users

router.get('/all', async (req, res) => {

    try {

        //Getting All users from MongoDB

        const users = await User.find({});

        // res.status(200).json(users);

  

        //Response Back

        res.status(200).json({ message: "User route hit", users });

    } catch (error) {

        res.status(500).json({ error: error.message });

    }

});

  

// 1. POST Data

router.post('/register', async (req, res) => {

    try {

        const { fullName, username, email } = req.body;

        // Checking if user exists to avoid duplicates in MongooseDB

        const existingUser = await User.findOne({ $or: [{ username }, { email }] });

        if (existingUser) {

            return res.status(409).json({ message: "Username or email already exists" });

        }

  

        // Creating a new user in the database using your Mongoose Model

        const newUser = new User({ fullName, username, email });

        await newUser.save();

        //Response Back

        res.status(201).json({ message: `${newUser} registered successfully` });

    } catch (error) {

        res.status(500).json({ error: error.message });

    }

});

  

module.export = router;
```