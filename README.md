# LiveProject

## Introduction
Over the past two weeks of my time at The Tech Academy i've been working on a remake of the classic arcade game "Donkey Kong" as a part of a larger project where other students re-create classic games using C# and Unity. This project as a whole was a great learning experience for me as I got to experience what it's like to develop a game from scratch, fix bugs, and add features. I worked on several stories throughout the project including level design, character and opposition scripting and adding a couple animations too. Over the course of the project I also got a lot of experience with project management and version control.

## Player Scripting
Story two was all about scripting the behavior of the character, below is part of the script for the player movement (which is only horizontal movement) and the jumping mechanic as well as the animators for the two.

    moveHorizontal = Input.GetAxisRaw("Horizontal");

        animator.SetFloat("Speed", Mathf.Abs(moveHorizontal)); 

        playerBody.velocity = new Vector2(moveHorizontal * speed, playerBody.velocity.y);

        if (Input.GetButtonDown("Jump") && IsGrounded())
        {                                   
            if (isJumping == false)
            {
                isJumping = true;
                float jump = 4f;
                playerBody.velocity = Vector2.up * jump;
                animator.SetBool("IsJumping", true);
            }                            
        }

## Opposition Behavior
Story three was about scripting the behavior of the enemy and how they would interact with the player. The only opposition behavior for my game remake was the spawning of the barrels that Donkey Kong would throw. Using a coroutine I am able to randomize the rate at which Donkey Kong throws the barrels making it a little more difficult for the player to time the jumps on the heighest platform.

      void Start()
    {
        StartCoroutine(barrelWave());
    }

    private void spawnBarrel()
    {
        GameObject a = Instantiate(barrelPrefab) as GameObject;
    }

    IEnumerator barrelWave()
    {
        while (true)
        {
            yield return new WaitForSeconds(Random.Range(.5f, 2.5f));
            spawnBarrel();
        }        
    }
    
## Other Skills Learned
* Problem solving
   * As I worked through the project a lot of bugs and problems arose. Learning to problem solve was a huge part of this project because befor starting, I hadn't made much with unity, all I really knew how to do was place some gameobjects and maybe write a simple script. But after finishing this project I learned a lot of valuable tips and tricks on how to get certain aspects of a game to behave the way I intended and if they didn't I would know how and what to search up for a nudge in the right direction.
* Asking for help
  * Another valuable thing I learned was to ask for help when I can't find and answer to a problem, in the begining, I didn't want to ask for help because I wanted to figure it out on my own and that would cause more problems then it would solve. Knowing when to reach out for help is a very valuable thing to know, especially when you're still learning how to do a lot of things.
    
