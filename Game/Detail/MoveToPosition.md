```
using System.Collections;  
using System.Collections.Generic;  
using Sirenix.OdinInspector;  
using UnityEngine;  
  
public class TestMove : MonoBehaviour  
{  
    private Rigidbody2D m_rigidbody2D;  
    private float m_Horizontal = 0;  
    private float m_Vertical = 0;  
    private bool isRool = false;  
    public float m_Speed = 5;  
    public float m_RoolSpeed = 5;  
    public float m_RoolRange = 10;  
    void Awake()  
    {        m_rigidbody2D = GetComponent<Rigidbody2D>();  
    }    [Button]  
    public void Move()  
    {        m_rigidbody2D.velocity = new Vector2(m_Horizontal, m_Vertical);  
    }  
    public void Rool()  
    {        Rooling = true;  
        StartCoroutine(RoolToPosition(transform.position,new Vector2(m_Horizontal,m_Vertical).normalized));  
    }  
    IEnumerator RoolToPosition(Vector2 position,Vector2 dir)  
    {        float minDistance = 0.2f;  
  
        Vector2 targetPosition = position + new Vector2(m_RoolRange,m_RoolRange) * dir;  
        while (Vector2.Distance(transform.position, targetPosition)>minDistance)  
        {            m_rigidbody2D.MovePosition(m_rigidbody2D.position + dir*m_RoolSpeed*Time.fixedDeltaTime);  
            yield return new WaitForFixedUpdate();  
        }    }  
    private bool Rooling = false;  
    void Update()  
    {        m_Horizontal = Input.GetAxis("Horizontal");  
        m_Vertical = Input.GetAxis("Vertical");  
  
        if (Input.GetKeyDown(KeyCode.LeftShift))//这里是个trigger 属性  
        {  
            Rool();  
        }        else  
        {  
            Move();  
        }    }}
```